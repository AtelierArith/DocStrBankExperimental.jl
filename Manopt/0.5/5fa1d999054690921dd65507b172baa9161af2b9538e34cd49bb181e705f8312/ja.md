```
StopWhenPopulationConcentrated <: StoppingCriterion
```

[`NelderMead`](@ref) の停止基準で、以下の条件が満たされたときに停止することを示します。

  * 最初のコスト値と残りのコスト値との最大距離
  * 最初の人口点と残りの人口点との最大距離

それぞれが特定の許容値 `tol_f` および `tol_p` を下回るときです。

# コンストラクタ

```
StopWhenPopulationConcentrated(tol_f::Real=1e-8, tol_x::Real=1e-8)
```
