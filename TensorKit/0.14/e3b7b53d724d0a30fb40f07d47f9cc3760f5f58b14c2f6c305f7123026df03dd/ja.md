```
transpose!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap,
           (p₁, p₂)::Index2Tuple)
    -> tdst
```

`tsrc`のインデックスを転置した結果を`tdst`に書き込みます。`tdst`のコドメインとドメインはそれぞれ`tsrc`の`p₁`と`p₂`のインデックスに対応します。新しいインデックス位置は、インデックスが交差しないように到達可能である必要があります。すなわち、置換`(p₁..., reverse(p₂)...)`は`(codomainind(tsrc)..., reverse(domainind(tsrc))...)`の循環置換を構成する必要があります。

新しいテンソルを作成するには[`transpose`](@ref)を、より一般的なバージョンには[`add_transpose!`](@ref)を参照してください。
