```
loadindex(filename::AbstractString, db::Union{Nothing,AbstractDatabase}=nothing; kwargs...)
```

`filename` からインデックスを読み込みます。`db` が指定されている場合、読み込まれたインデックスのデータセットがそれに置き換えられます。

# 引数

  * `db`: 読み込み後に指定された `db` でインデックスデータベースを置き換えます
  * `parent="/"`: インデックスの親グループ
