```
RazborovModel{T<:Flag, N, D} <: AbstractFlagModel{T, N, D}
```

完全に対称性が削減されていないRazborovスタイルのモデルです。TがInducedFlagである場合、階層はFlagmaticで実装されているものと同じです。Tが誘導されていない場合、ラベル付き頂点のみにモービウス変換が適用されます。結果として得られる階層は通常の階層の基底変換であり、同じ境界を返しますが、非誘導フラグで表現されます。
