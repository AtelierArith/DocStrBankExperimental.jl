```
childrentype(::Type{T})
childrentype(n)
```

ツリー ノード `n` またはその型 `T` の子供の型（子供の *コレクション*、個々の子供ではない）を示します。 [`children`](@ref) はこの型のオブジェクトを返すべきです。

`childrentype` がノードの型だけから推測できる場合、型 `::Type{T}` の定義が優先されます（後者はそれにフォールバックします）。

**オプション**: ほとんどの場合、[`childtype`](@ref) が代わりに使用されます。 `childtype` が定義されていない場合は、`eltype ∘ childrentype` にフォールバックします。
