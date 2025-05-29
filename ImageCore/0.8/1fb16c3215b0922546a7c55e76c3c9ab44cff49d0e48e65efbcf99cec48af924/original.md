```
scaleminmax(min, max) -> f
scaleminmax(T, min, max) -> f
```

Return a function `f` which maps values less than or equal to `min` to 0, values greater than or equal to `max` to 1, and uses a linear scale in between. `min` and `max` should be real values.

Optionally specify the return type `T`. If `T` is a colorant (e.g., RGB), then scaling is applied to each color channel.

# Examples

## Example 1

```julia
julia> f = scaleminmax(-10, 10)
(::#9) (generic function with 1 method)

julia> f(10)
1.0

julia> f(-10)
0.0

julia> f(5)
0.75
```

## Example 2

```julia
julia> c = RGB(255.0,128.0,0.0)
RGB{Float64}(255.0,128.0,0.0)

julia> f = scaleminmax(RGB, 0, 255)
(::#13) (generic function with 1 method)

julia> f(c)
RGB{Float64}(1.0,0.5019607843137255,0.0)
```

See also: [`takemap`](@ref).
