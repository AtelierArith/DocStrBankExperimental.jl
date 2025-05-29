```
withgradient(f, args...)
```

Returns both the value of the function and the [`gradient`](@ref), as a named tuple.

By default, `Flux.withgradient` calls Zygote. If you load Enzyme, then other methods become available.

# Example

```
julia> y, ∇ = withgradient(/, 1, 2)
(val = 0.5, grad = (0.5, -0.25))

julia> ∇ == gradient(/, 1, 2)
true
```

Allows you to capture auxillary outputs, in addition to the scalar used by `gradient`. To do this, `f` must return a Tuple or NamedTuple. Then it calculates `grad = gradient(first∘f, args...) but returns the whole`val = f(args...)`:

```jldoctest; setup=:(using Zygote)
julia> withgradient([1,2,4]) do x
          z = 1 ./ x
          sum(z), z  # here z is an auxillary output
       end
(val = (1.75, [1.0, 0.5, 0.25]), grad = ([-1.0, -0.25, -0.0625],))

julia> withgradient(3.0, 4.0) do x, y
          (div = x/y, mul = x*y)
       end
(val = (div = 0.75, mul = 12.0), grad = (0.25, -0.1875))
```
