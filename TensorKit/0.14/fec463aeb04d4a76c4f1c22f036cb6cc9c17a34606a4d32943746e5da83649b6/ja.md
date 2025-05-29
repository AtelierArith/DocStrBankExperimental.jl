```
transpose(tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple;
          copy::Bool=false)
    -> tdst::TensorMap
```

テンソル `tdst` は、`tsrc` のインデックスを転置することによって得られます。`tdst` のコドメインとドメインは、それぞれ `tsrc` の `p₁` と `p₂` のインデックスに対応します。新しいインデックスの位置は、インデックスが交差しないように到達可能である必要があります。すなわち、置換 `(p₁..., reverse(p₂)...)` は、`(codomainind(tsrc)..., reverse(domainind(tsrc))...)` の循環置換を構成する必要があります。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合、常にコピーが作成されます。

既存の宛先に置換するには、[permute!](@ref) および [`add_permute!`](@ref) を参照してください。
