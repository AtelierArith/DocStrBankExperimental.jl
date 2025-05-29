```
predict(phd::PHDFilter, b0::GaussianMixture)
```

Make a prediction on next state based on PHD dynamics

Arguments:

  * `phd::PHDFilter` PHD filter to step through. [PHD Filter]
  * `b0::GaussianMixture` Prior state distribution. [Gaussian Mixture]

Returns:

  * `bp::GaussianMixture` Predicted next state distribution. [Gaussian Mixture]

References:

1. Vo, B. N., & Ma, W. K. (2006). The Gaussian mixture probability hypothesis

density filter. IEEE Transactions on signal processing, 54(11), 4091-4104.
