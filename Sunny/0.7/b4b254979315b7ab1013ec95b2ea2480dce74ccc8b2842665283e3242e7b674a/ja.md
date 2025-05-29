```
set_exchange_at!(sys::System, J, site1::Site, site2::Site; biquad=0, offset=nothing)
```

2つの[`Site`](@ref)を接続する単一の結合に沿った交換相互作用$𝐒_i⋅J 𝐒_j$を設定します。結晶対称性は無視されます。この結合に対する以前の結合は上書きされます。システムは[`to_inhomogeneous`](@ref)を介して不均一な相互作用をサポートする必要があります。

同じ対称性を持つ値`(site1, site2, offset)`を見つけるには、[`symmetry_equivalent_bonds`](@ref)を使用して、均一なシステム内の特定の[`Bond`](@ref)に対して対称的に等しいものを見つけます。小さなシステムの場合、`offset`ベクトル（単位セルの倍数）は周期的なラッピングにおける曖昧さを解消します。

`J`と`biquad`を指定する詳細については、[`set_exchange!`](@ref)も参照してください。より一般的な結合には、代わりに[`set_pair_coupling_at!`](@ref)を使用してください。
