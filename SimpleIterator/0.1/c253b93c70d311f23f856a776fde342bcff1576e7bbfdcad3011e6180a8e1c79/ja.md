```
IteratorType(::Type{T})
```

型のイテレータ型を返します。この関数をオーバーロードして型のイテレータ型を定義します。この関数は型を返す必要があります。デフォルトの実装は `Any` です。この関数をオーバーロードして、`Base.length` や `Base.eltype` などの型に関連するイテレーションユーティリティを有効にします。[`iterator`](@ref) 関数が戻り値の型注釈と共に定義されている場合、この関数は自動的にオーバーロードされます。
