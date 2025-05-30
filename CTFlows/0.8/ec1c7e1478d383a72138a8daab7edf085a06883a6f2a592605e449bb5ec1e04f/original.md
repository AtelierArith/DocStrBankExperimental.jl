```julia
⋅(
    X::Function,
    f::Function
) -> CTFlows.var"#27#29"{CTFlows.VectorField{var"#s182", CTFlows.Autonomous, CTFlows.Fixed}, <:Function} where var"#s182"<:Function

```

Lie derivative of a scalar function along a function. In this case both functions will be considered autonomous and non-variable.

# Example

```@example
julia> φ = x -> [x[2], -x[1]]
julia> f = x -> x[1]^2 + x[2]^2
julia> (φ⋅f)([1, 2])
0
julia> φ = (t, x, v) -> [t + x[2] + v[1], -x[1] + v[2]]
julia> f = (t, x, v) -> t + x[1]^2 + x[2]^2
julia> (φ⋅f)(1, [1, 2], [2, 1])
MethodError
```
