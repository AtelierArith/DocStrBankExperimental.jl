```julia
@bind image WebcamInput(; kwargs...)
```

A webcam input. Provides the user with a small interface to select a camera and take a picture, the captured image is returned as a `Matrix{RGB}` via `@bind`. 

# How to use a `Matrix{RGB}`

The output type is of the type `Matrix{RGB{N0f8}}`, let's break that down:

  * `Matrix`: This is a 2D **Array**, which you can index like `img[10,20]` to get an entry, of type `RGB{N0f8}`.
  * `RGB` (from [ColorTypes.jl](https://github.com/JuliaGraphics/ColorTypes.jl)): a `struct` with fields `r` (Red), `g` (Green) and `b` (Blue), each of type `N0f8`. These are the digital 'channel' value that make up a color.
  * `N0f8` (from [FixedPointNumbers.jl](https://github.com/JuliaMath/FixedPointNumbers.jl)): a special type of floating point number that uses only 8 bits. Think of it as a `Float8`, rather than the usual `Float64`. You can use `Float64(x)` to convert to a normal `Float64`.

By default, a `Matrix{RGB}` will be displayed using text, but if you add 

```julia
import ImageShow, ImageIO
```

somewhere in your notebook, then Pluto will be able to display the matrix as a color image.

For more image manipulation capabilities, check out [`Images.jl`](https://github.com/JuliaImages/Images.jl).

# Keyword arguments

  * `help::Bool=true` by default, we display a little help message when you use `WebcamInput`. You can disable that here.
  * `default::Matrix{RGB{N0f8}}` set a default image, which is used until the user captures an image. Defaults to a **1x1 transparent image**.
  * `max_size::Int64` when given, this constraints the largest dimension of the image, while maintaining aspect ratio. A lower value has better performance.
  * `avoid_allocs::Bool=false` when set to `true`, we lazily convert the raw `Vector{UInt8}` camera data to a `AbstractMatrix{RGB{N0f8}}`, with zero allocations. This will lead to better performance, but the bound value will be an `AbstractMatrix`, not a `Matrix`.

# Examples

```julia
@bind image WebcamInput()
```

Let's see what we captured:

```julia
import ImageShow, ImageIO
```

```julia
image
```

Let's look at the **size** of the matrix:

```julia
size(image)
```

To get the **green** channel value of the **top right** pixel of the image:

```julia
image[1, end].g
```
