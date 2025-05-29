```
SmallSet{N,T} <: AbstractSmallSet{N,T}

SmallSet{N,T}()
SmallSet{N,T}(itr; unique = itr isa AbstractSet)
```

要素型 `T` を持ち、最大 `N` エントリを格納できる不変集合です。すべてのエントリは、構築時に提供されたイテレータ `itr` から来ます。

要素型が省略された場合、可能であればイテレータから推論されます。`unique` が `true` に設定されている場合、`itr` の要素は異なるものと見なされます。

関連情報として [`AbstractSmallSet`](@ref)、[`MutableSmallSet`](@ref) を参照してください。
