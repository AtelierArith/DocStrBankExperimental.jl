```julia
Lift(
    X::Function;
    autonomous,
    variable
) -> CTFlows.var"#19#23"{<:Function}

```

関数のLiftを返します。依存関係はブール値 : autonomous と variable で指定されます。

# 例

```@example
julia> H = Lift(x -> 2x)
julia> H(1, 1)
2
julia> H = Lift((t, x, v) -> 2x + t - v, autonomous=false, variable=true)
julia> H(1, 1, 1, 1)
2
```
