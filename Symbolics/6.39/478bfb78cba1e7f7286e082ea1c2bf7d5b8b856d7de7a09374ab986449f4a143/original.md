```
rootfunction(f)
```

Given a function `f` with a discontinuity or discontinuous derivative, return the rootfinding function of `f`. The rootfinding function `g` takes the same arguments as `f`, and is such that `f` can be described as a piecewise function based on the sign of `g`, where each piece is continuous and has a continuous derivative. The pieces are obtained using `left_continuous_function(f)` and `right_continuous_function(f)`.

More formally,

```julia
f(args...) = if g(args...) < 0
    left_continuous_function(f)(args...)
else
    right_continuous_function(f)(args...)
end
```

For example, if `f` is `max(x, y)`, the root function is `(x, y) -> x - y` with `left_continuous_function` as `(x, y) -> y` and `right_continuous_function` as `(x, y) -> x`.

See also: [`left_continuous_function`](@ref), [`right_continuous_function`](@ref).
