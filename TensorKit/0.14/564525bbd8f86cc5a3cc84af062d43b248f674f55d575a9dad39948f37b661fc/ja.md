```
repartition(tsrc::AbstractTensorMap{S}, N₁::Int, N₂::Int; copy::Bool=false) where {S}
    -> tdst::AbstractTensorMap{S,N₁,N₂}
```

テンソル `tdst` を返します。これは `t` のインデックスを再分配することによって得られます。`tdst` のコドメインとドメインは、それぞれ `t` の最初の `N₁` と最後の `N₂` の空間に対応します。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合は、常にコピーが作成されます。

既存の宛先に再分配するには、[repartition!](@ref) を参照してください。
