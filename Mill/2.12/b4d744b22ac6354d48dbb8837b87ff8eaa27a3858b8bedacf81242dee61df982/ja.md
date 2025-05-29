```
preimputing_dense(in, out, σ)
```

`Flux.Dense`のように、標準の行列の代わりに[`PreImputingMatrix`](@ref)を使用します。

# 例

```jldoctest
julia> d = preimputing_dense(2, 3)
[preimputing]Dense(2 => 3)  3 arrays, 11 params, 172 bytes

julia> typeof(d.weight)
PreImputingMatrix{Float32, Matrix{Float32}, Vector{Float32}}

julia> typeof(d.bias)
Vector{Float32} (alias for Array{Float32, 1})
```

関連項目: [`PreImputingMatrix`](@ref), [`postimputing_dense`](@ref), [`PostImputingMatrix`](@ref).
