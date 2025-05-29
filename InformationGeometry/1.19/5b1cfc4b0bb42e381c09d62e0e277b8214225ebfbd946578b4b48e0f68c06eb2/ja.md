```
loglikelihood(DM::DataModel, θ::AbstractVector) -> Real
```

データモデル `DataModel` とパラメータ設定 $\theta$ が与えられたとき、尤度 $L$ の対数、すなわち $\ell(\mathrm{data} \, | \, \theta) \coloneqq \mathrm{ln} \big( L(\mathrm{data} \, | \, \theta) \big)$ を計算します。
