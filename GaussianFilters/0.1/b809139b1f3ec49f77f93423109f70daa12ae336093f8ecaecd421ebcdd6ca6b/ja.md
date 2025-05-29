```
predict(phd::PHDFilter, b0::GaussianMixture)
```

PHDダイナミクスに基づいて次の状態を予測します

引数:

  * `phd::PHDFilter` ステップを踏むPHDフィルタ。 [PHD Filter]
  * `b0::GaussianMixture` 事前状態分布。 [Gaussian Mixture]

戻り値:

  * `bp::GaussianMixture` 予測された次の状態分布。 [Gaussian Mixture]

参考文献:

1. Vo, B. N., & Ma, W. K. (2006). The Gaussian mixture probability hypothesis

density filter. IEEE Transactions on signal processing, 54(11), 4091-4104.
