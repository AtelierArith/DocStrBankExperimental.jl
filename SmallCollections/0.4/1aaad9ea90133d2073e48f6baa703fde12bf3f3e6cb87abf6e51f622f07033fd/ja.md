```
SmallCollections.isfasttype(::Type{T}) where T -> Bool
```

要素の型 `T` が高速（例えば、ベクトル化された）操作を許可する場合は `true` を返します。

デフォルトでは、`Base.HWReal`、`Bool`、`Char`、および `Enum` 型は高速と見なされ、`Complex`、`Pair`、`Tuple`、`NamedTuple` および高速コンポーネントを持つ `Ref` も含まれます。

`Base.HWReal` を参照してください。
