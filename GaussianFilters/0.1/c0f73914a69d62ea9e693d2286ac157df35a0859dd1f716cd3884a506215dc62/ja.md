```
update(phd::PHDFilter, b0::GaussianMixture, Z::Vector{AbstractVector},
	T::Real, U::Real, J_max::Integer)
```

GMPHDフィルタを使用して更新ステップを実行します。

引数:

  * `phd::PHDFilter` ステップを実行するPHDフィルタ。[PHD Filter]
  * `b0::GaussianMixture` 事前状態分布。[Gaussian Mixture]
  * `Z::Matrix` 測定値の行列。[Measurements]
  * `T::Real` 切断閾値。重みがT未満の分布を削除します。
  * `U::Real` マージ閾値。(μ*1-μ*2)^T * Σ^-1 * (μ*1-μ*2) < Uの場合にマージします。
  * `J_max::Integer` 最大特徴数

戻り値:

  * `bn::GaussianMixture` 最初の戻り値を説明します。[Gaussian Mixture]

参考文献:

1. Vo, B. N., & Ma, W. K. (2006). ガウス混合確率仮説密度フィルタ。IEEE Transactions on signal processing, 54(11), 4091-4104.
