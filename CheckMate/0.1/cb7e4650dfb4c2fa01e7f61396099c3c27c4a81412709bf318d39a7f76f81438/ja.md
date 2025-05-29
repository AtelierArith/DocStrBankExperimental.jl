```
failing_rows(summary::CheckSummary, check_name::String)::Vector{Int}
```

特定の名前付きチェックに対して失敗した行のインデックスを取得します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。
  * `check_name::String`: 失敗した行を取得する特定のチェックの名前。

# 戻り値

指定されたチェックに失敗した行のインデックスのベクター。

# 例外

  * 指定されたチェック名がサマリーに見つからない場合は `ErrorException` をスローします。

# 例

```julia
failed_indices = failing_rows(summary, "column_type_check")  # Returns [3, 7, 10, ...]
```
