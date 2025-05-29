```
tt_load(date::Union{String,Date}; use_cache=true)
```

特定の日付のTidyTuesdayデータセットをロードします。DataFrameのNamedTupleを返します。

# 引数

  * `date`: "YYYY-MM-DD"形式の日付文字列またはDateオブジェクト
  * `use_cache`: 利用可能な場合にキャッシュデータを使用するかどうか（デフォルト: true）

# 返り値

各フィールドがデータセットを含むDataFrameであるNamedTuple。
