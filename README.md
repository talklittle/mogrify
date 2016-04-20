# Mogrify

An Elixir wrapper for ImageMagick command line.

## Requirements

You must have ImageMagick installed of course.

## Installation

Add this to your `mix.exs` file, then run `mix do deps.get, deps.compile`:

```elixir
  {:mogrify, "~> 0.2"}
```

## Examples

Thumbnailing:

```elixir
  import Mogrify

  # This does operations on a copy of the file:
  open("input.jpg") |> resize("100x100") |> save
  # To overwrite the original:
  open("input.jpg") |> resize("100x100") |> save(in_place: true)
  # Resize to fill
  open("input.jpg") |> resize_to_fill("450x300") |> save
  # Resize to limit
  open("input.jpg") |> resize_to_limit("200x200") |> save
  # Extent
  open("input.jpg") |> extent("500x500") |> save
```

Converting:

```elixir
  import Mogrify

  image = open("input.jpg") |> format("png") |> save
  IO.inspect(image) # => %Image{path: "/tmp/568550-input.png", ext: ".png", format: "png", height: "292", width: "300"}
```

Getting info:

```elixir
  import Mogrify

  image = open("input.jpg") |> verbose
  IO.inspect(image) # => %Image{path: "input.jpg", ext: ".jpg", format: "jpeg", height: "292", width: "300"}
```
