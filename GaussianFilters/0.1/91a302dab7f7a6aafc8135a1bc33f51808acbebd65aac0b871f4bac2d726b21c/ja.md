```
prune(b::GaussianMixture, T::Real, U::Real, J_max::Integer)
```

後方ガウス混合次PHD状態をプルーニングします

引数:

  * `b::GaussianMixture` 後方状態分布。 [Gaussian Mixture]
  * `T::Real` 切断閾値。 重みがT未満の分布を削除します
  * `U::Real` 統合閾値。 (μ*1-μ*2)^T * Σ^-1 * (μ*1-μ*2) < U の場合に統合します
  * `J_max::Integer` 最大特徴数

```
