```
failing_rows(summary::CheckSummary)::Vector{Int}
```

すべてのチェックにおけるユニークな失敗行インデックスを取得します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

任意のチェックに失敗したユニークな行インデックスのソートされたベクター。

# 例

```julia
all_failed_indices = failing_rows(summary)  # Returns [1, 2, 5, 8, ...]
```
