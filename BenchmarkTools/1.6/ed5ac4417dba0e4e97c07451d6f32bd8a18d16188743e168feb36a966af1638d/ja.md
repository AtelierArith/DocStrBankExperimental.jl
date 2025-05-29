```
@ballocations expression [other parameters...]
```

Juliaに含まれる`@allocations`マクロに似て、このマクロは式を評価し、結果の値を破棄し、その実行中に行われた合計の割り当て数を返します。

`@allocations`とは異なり、`BenchmarkTools`パッケージの`@benchmark`マクロを使用し、`@benchmark`と同じ追加パラメータをすべて受け入れます。返される割り当て数は、ベンチマーク中に測定された*最小*経過時間を持つ試行に対応します。
