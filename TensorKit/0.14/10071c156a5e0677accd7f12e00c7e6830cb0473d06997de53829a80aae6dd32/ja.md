```
braid!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap,
       (p₁, p₂)::Index2Tuple, levels::Tuple)
    -> tdst
```

`tsrc`のインデックスをブレードする結果を`tdst`に書き込みます。`tdst`のコドメインとドメインは、それぞれ`tsrc`の`p₁`と`p₂`のインデックスに対応します。ここで、`levels`は`numind(tsrc)`の長さを持つタプルで、`tsrc`のインデックスにレベルまたは高さを割り当て、どのインデックスが他のインデックスと入れ替わる際に上にブレードするか下にブレードするかを決定します。

新しいテンソルを作成するための[`braid`](@ref)や、より一般的なバージョンの[`add_braid!`](@ref)を参照してください。
