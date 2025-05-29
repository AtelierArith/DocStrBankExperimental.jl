```
ProductSector{T<:SectorTuple}
```

セクターのデリーニュテンソル積を表します。型パラメータ `T` は構成セクターのタプルです。`ProductSector` を構築する推奨方法は、構成要素に対して [`deligneproduct`](@ref) (`⊠`) 演算子を使用することです。
