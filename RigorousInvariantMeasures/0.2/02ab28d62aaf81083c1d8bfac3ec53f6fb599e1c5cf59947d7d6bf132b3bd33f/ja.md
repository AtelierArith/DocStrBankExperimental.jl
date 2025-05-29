```
strong_norm(B::Basis)
```

基底の強ノルムの型を返します

# 例

```jldoctest
julia> using RigorousInvariantMeasures

julia> B = Ulam(1024)
Ulam{LinRange{Float64, Int64}}(LinRange{Float64}(0.0, 1.0, 1025))

julia> strong_norm(B)
TotalVariation
```
