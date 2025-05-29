```
execution_time(summary::CheckSummary)::Float64
```

すべてのチェックの合計実行時間を取得します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

秒単位の合計実行時間。

# 例

```julia
time = execution_time(summary)  # 秒単位の実行時間を返します
```
