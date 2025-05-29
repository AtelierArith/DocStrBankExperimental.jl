```
measure(phd::PHDFilter, bp::GaussianMixture, Z::Vector{AbstractVector})
```

予測されたPHD次状態に対して測定更新を行います。

引数:

  * `phd::PHDFilter` ステップを踏むPHDフィルタ。 [PHD Filter]
  * `bp::GaussianMixture` 事前状態分布。 [Gaussian Mixture]
  * `Z::Vector{AbstractVector}` 測定の配列。 [Measurements]

戻り値:

  * `bm::GaussianMixture` 最初の戻り値を説明します。 [Gaussian Mixture]

参考文献:

1. Vo, B. N., & Ma, W. K. (2006). The Gaussian mixture probability hypothesis

density filter. IEEE Transactions on signal processing, 54(11), 4091-4104.
