```
total_failures(summary::CheckSummary)::Int
```

すべてのチェックにわたる失敗した行の合計数を計算します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

すべてのチェックにわたる検証に失敗した行の合計数。

# 例

```julia
total_failed = total_failures(summary)  # 失敗した行の合計数を返します
```
