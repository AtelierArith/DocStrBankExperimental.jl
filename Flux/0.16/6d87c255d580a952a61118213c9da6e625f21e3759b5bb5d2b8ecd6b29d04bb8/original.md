```
gradient(f, args...)
```

Returns a tuple containing `∂f/∂x` for each argument `x`, the derivative (for scalar `x`) or the gradient. If no gradient is defined, `∂f/∂x` will be `nothing`.

`f(args...)` must be a real number, see [`Zygote.jacobian`](@ref) for array output.

By default, `Flux.gradient` calls Zygote. If you load Enzyme, then other methods become available.

See also [`withgradient`](@ref) to keep the value `f(args...)`.

# Examples

```
julia> Flux.gradient(*, 2.0, 3.0, 5.0)
(15.0, 10.0, 6.0)

julia> Flux.gradient(x -> sum(abs2,x), [7.0, 11.0, 13.0])
([14.0, 22.0, 26.0],)

julia> Flux.gradient([7, 11], 0, 1) do x, y, d
         p = size(x, d)
         sum(x.^p .+ y)
       end
([14.0, 22.0], 2.0, nothing)
```
