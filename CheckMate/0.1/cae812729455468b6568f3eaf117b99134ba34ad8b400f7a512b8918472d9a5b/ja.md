```
failing_rows(result::CheckResult)::Vector{Int}
```

特定のチェック結果に対して失敗した行のインデックスを取得します。

# 引数

  * `result::CheckResult`: 単一のチェックの結果オブジェクト。

# 戻り値

チェックに失敗した行のインデックスのベクター。

# 例

```julia
failed_indices = failing_rows(result)  # Returns [2, 5, 8, ...]
```
