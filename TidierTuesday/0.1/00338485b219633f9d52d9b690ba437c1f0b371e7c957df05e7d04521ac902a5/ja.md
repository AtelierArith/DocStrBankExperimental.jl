```
tt_load(year::Integer, week::Integer; use_cache=true)
```

特定の年と週のTidyTuesdayデータセットをロードします。DataFrameのNamedTupleを返します。

# 引数

  * `year`: 年（例: 2024）
  * `week`: 週番号（1-52）
  * `use_cache`: 利用可能な場合にキャッシュデータを使用するかどうか（デフォルト: true）

# 返り値

各フィールドがデータセットを含むDataFrameであるNamedTuple。
