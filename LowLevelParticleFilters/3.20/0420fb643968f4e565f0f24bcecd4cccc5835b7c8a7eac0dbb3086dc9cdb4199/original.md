```
R = double_integrator_covariance_smooth(Ts, σ2=1)
```

Returns the covariance matrix of a discrete-time integrator with continuous noise as input. Assumes the state [x; ẋ]. `Ts` is the sample time. `σ2` scales the covariance matrix with the variance of the noise.

This matrix is full rank, but can be well approximated by a rank-1 matrix as `double_integrator_covariance(h, σ2) ./ Ts`. I.e., to make use of a single random number per step for augmented UKFs, but be have a resulting covariance dynamics that is approximately invariant to the sample interval, you can use `double_integrator_covariance(h, σ2) ./ Ts` instead of this function.
