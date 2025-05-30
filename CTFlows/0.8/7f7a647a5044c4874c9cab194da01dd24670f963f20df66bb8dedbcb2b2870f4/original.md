```julia
Lift(
    X::Function;
    autonomous,
    variable
) -> CTFlows.var"#19#23"{<:Function}

```

Return the Lift of a function. Dependencies are specified with boolean : autonomous and variable.

# Example

```@example
julia> H = Lift(x -> 2x)
julia> H(1, 1)
2
julia> H = Lift((t, x, v) -> 2x + t - v, autonomous=false, variable=true)
julia> H(1, 1, 1, 1)
2
```
