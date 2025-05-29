```
calculate_primal_feasibility(algorithm::SchwarzAlgorithm) -> Vector{Float64}
```

アルゴリズムのグラフ上で定義されたリンク制約のプライマル可行性を評価します。これは、サブプロブレムの解に基づいてリンク制約とその期待値との間の残差をチェックすることによって行われます。

Args:

  * `algorithm::SchwarzAlgorithm`: グラフとリンク制約を含むアルゴリズムオブジェクト。

Returns:     リンク制約のプライマル残差のベクトル。
