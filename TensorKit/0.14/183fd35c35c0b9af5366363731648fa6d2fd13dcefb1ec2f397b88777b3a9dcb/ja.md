```
braid(tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple, levels::IndexTuple;
      copy::Bool = false)
    -> tdst::TensorMap
```

テンソル `tdst` は、`tsrc` のインデックスをブレイドすることによって得られます。`tdst` のコドメインとドメインは、それぞれ `tsrc` の `p₁` と `p₂` のインデックスに対応します。ここで、`levels` は `numind(tsrc)` の長さを持つタプルで、`tsrc` のインデックスにレベルまたは高さを割り当て、どのインデックスが他のインデックスと入れ替わる際に上にブレイドするか下にブレイドするかを決定します。

`copy=false` の場合、`tdst` は可能な限り `tsrc` とデータを共有することがあります。そうでない場合、常にコピーが作成されます。

既存の宛先にブレイドするには、[braid!](@ref) および [`add_braid!`](@ref) を参照してください。
