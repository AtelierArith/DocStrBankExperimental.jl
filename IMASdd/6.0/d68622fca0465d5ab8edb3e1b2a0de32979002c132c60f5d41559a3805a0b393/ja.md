```
imas2json(@nospecialize(ids::Union{IDS,IDSvector}), filename::AbstractString; freeze::Bool=false, strict::Bool=false, indent::Int=0, kw...)
```

指定された `filename` で IMAS データ構造を JSON ファイルに保存します。

# 引数

  * `freeze` は式を評価します
  * `strict` は ITER IMAS のみに厳密に存在するフィールドをダンプします
  * `kw...` 引数は `JSON.print` 関数に渡されます
