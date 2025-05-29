```
permute(tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple;
        copy::Bool=false)
    -> tdst::TensorMap
```

テンソル `tdst` は `tsrc` のインデックスを並べ替えることによって得られます。`tdst` のコドメインとドメインはそれぞれ `tsrc` の `p₁` と `p₂` のインデックスに対応します。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合、常にコピーが作成されます。

既存の宛先に並べ替えるには、[permute!](@ref) と [`add_permute!`](@ref) を参照してください。
