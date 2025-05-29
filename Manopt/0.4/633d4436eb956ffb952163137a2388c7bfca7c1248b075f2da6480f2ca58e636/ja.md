```
StopWhenPopulationStronglyConcentrated{TParam<:Real} <: StoppingCriterion
```

すべての座標の標準偏差が `tol` より小さく、かつ `σ * p_c` のノルムが `tol` より小さい場合に停止します。これは [Hansen:2023](@cite) の `TolX` 条件に対応します。

# フィールド

  * `tol` チェックするための許容誤差
  * `at_iteration` 許容誤差が満たされたイテレーション $i \geq 0$ を示す内部フィールド

# コンストラクタ

```
StopWhenPopulationStronglyConcentrated(tol::Real)
```
