```julia
Poisson(
    f::Function,
    g::Function;
    autonomous,
    variable
) -> CTFlows.Hamiltonian

```

二つの関数のポアソン括弧 : {f, g} = Poisson(f, g) 依存関係はブール値で指定されます : autonomous と variable.

# 例

```@example
julia> f = (x, p) -> x[2]^2 + 2x[1]^2 + p[1]^2
julia> g = (x, p) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1]
julia> Poisson(f, g)([1, 2], [2, 1])
-20            
julia> f = (t, x, p, v) -> t*v[1]*x[2]^2 + 2x[1]^2 + p[1]^2 + v[2]
julia> g = (t, x, p, v) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1] + t - v[2]
julia> Poisson(f, g, autonomous=false, variable=true)(2, [1, 2], [2, 1], [4, 4])
-76
```
