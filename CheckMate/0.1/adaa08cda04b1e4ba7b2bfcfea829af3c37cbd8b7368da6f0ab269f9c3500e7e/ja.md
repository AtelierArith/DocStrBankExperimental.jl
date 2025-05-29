```
passed_checks(summary::CheckSummary)::Vector{String}
```

すべてのチェックが成功した名前を取得します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

成功したチェック名のベクター。

# 例

```julia
checks = passed_checks(summary)  # Returns ['check3', 'check4', ...]
```
