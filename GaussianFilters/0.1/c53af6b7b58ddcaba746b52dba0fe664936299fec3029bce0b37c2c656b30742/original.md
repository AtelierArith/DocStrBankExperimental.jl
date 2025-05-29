```
measure(phd::PHDFilter, bp::GaussianMixture, Z::Vector{AbstractVector})
```

Perform a measurement update on a predicted PHD next state.

Arguments:

  * `phd::PHDFilter` PHD filter to step through. [PHD Filter]
  * `bp::GaussianMixture` Prior state distribution. [Gaussian Mixture]
  * `Z::Vector{AbstractVector}` Array of measurements. [Measurements]

Returns:

  * `bm::GaussianMixture` Describe first return value. [Gaussian Mixture]

References:

1. Vo, B. N., & Ma, W. K. (2006). The Gaussian mixture probability hypothesis

density filter. IEEE Transactions on signal processing, 54(11), 4091-4104.
