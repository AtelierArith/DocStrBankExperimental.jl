```
permute!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple)
    -> tdst
```

`tsrc`のインデックスを並べ替えた結果を`tdst`に書き込みます。`tdst`のコドメインとドメインは、それぞれ`tsrc`の`p₁`と`p₂`のインデックスに対応します。

新しいテンソルを作成するには[`permute`](@ref)を、より一般的なバージョンについては[`add_permute!`](@ref)を参照してください。
