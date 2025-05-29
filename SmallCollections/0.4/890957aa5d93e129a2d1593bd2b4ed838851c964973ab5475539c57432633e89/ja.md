```
MutableSmallSet{N,T} <: AbstractSmallSet{N,T}

MutableSmallSet{N,T}()
MutableSmallSet{N,T}(itr; unique = itr isa AbstractSet)
```

要素型 `T` を持ち、最大 `N` エントリを格納できるセットです。このセットは可変で、Julia のセットインターフェースを実装しています。

要素型が省略された場合、可能であればイテレータから推論されます。`unique` が `true` に設定されている場合、`itr` の要素は異なるものと見なされます。

詳細は [`AbstractSmallSet`](@ref)、[`SmallSet`](@ref) を参照してください。
