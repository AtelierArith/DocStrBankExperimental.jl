```
calculate_dual_feasibility(algorithm::SchwarzAlgorithm) -> Vector{Float64}
```

アルゴリズムのグラフ上で定義されたリンク制約の双対可行性を評価します。各リンク制約について、関数はサブ問題間の最大および最小双対値の差を計算します。

Args:

  * `algorithm::SchwarzAlgorithm`: グラフとリンク制約を含むアルゴリズムオブジェクト。

Returns:     リンク制約に対する双対残差のベクトル。
