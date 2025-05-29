```
failed_checks(summary::CheckSummary)::Vector{String}
```

すべてのチェックの中で合格しなかったチェックの名前を取得します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

失敗した（合格しなかった）チェックの名前のベクター。

# 例

```julia
checks = failed_checks(summary)  # Returns ['check1', 'check2', ...]
```
