```
Try{T} = Union{Const{<:Exception}, Identity{T}}
@Try(error("something happend")) isa Const(<:Thrown{ErrorException})
@Try(:successfull) == Identity(:successfull)
```

[`Either`](@ref) の特定のケースで、Failure は常に Exception です。これは、try-catch 構文の代わりとして使用でき、エラーが適切に定義された型でキャプチャされるため、非常に柔軟なエラーハンドリングを可能にします。エラーを他の値のように扱うことが本当に便利なことが多く（例外にのみ適用される追加の try-catch 構文を必要としません）、この方法が役立ちます。

単一要素コンテナを表すために [`Identity`](@ref) を再利用し、スローされる Exception として `Const(<:Exception)` を使用します。
