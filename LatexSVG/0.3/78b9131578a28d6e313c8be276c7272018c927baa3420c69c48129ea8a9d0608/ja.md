```
add_preamble!(pre::AbstractString...; reset=false)
```

デフォルトの前文の上に前文ステートメントを追加します。`pre` は任意の数の `AbstractString` です。

すでにいくつかの前文ステートメントがあり、新しいステートメントを追加する前にそれらを削除したい場合は、`reset=true` を渡してください。
