```
SymmetryVectors(
    nvs :: AbstractVector{<:Integer},
    irlabs_nv :: AbstractVector{<:AbstractString},
    lgirsd :: AbstractDict{String, <:AbstractVector{LGIrrep{D}}}) 
                                                        --> Vector{SymmetryVector{D}}
```

[`SymmetryVector(::AbstractVector{<:Integer}, ::AbstractVector{<:AbstractString}, ::AbstractDict)](@ref)と同様ですが、単一のベクトルではなく、異なる生の重複ベクトル `nvs` のベクトルに対して、`Vector{SymmetryVector{D}}` を返します。

返される `SymmetryVector` の `ns` は、すべての `n` と `n′` に対して `irreps(n) === irreps(n′)` となるように、同じ基盤となる irrep 情報を共有します。
