```
permute(f::FusionTree, p::NTuple{N, Int}) -> <:AbstractDict{typeof(t), <:Number}
```

フュージョンツリー `f` の非結合インデックスの順序を入れ替え、その結果を出力ツリーと対応する係数の `<:AbstractDict` として返します。これは `BraidingStyle(sectortype(f)) isa SymmetricBraiding` である必要があります。
