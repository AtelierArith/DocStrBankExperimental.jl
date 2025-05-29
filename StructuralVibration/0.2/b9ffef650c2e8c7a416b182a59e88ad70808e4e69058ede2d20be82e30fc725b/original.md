```
GaussianPulse(F, tstart, duration, fc)
```

Struct to define a Gaussian pulse excitation signal

**Fields**

  * `F::Real`: Amplitude of the force [N]
  * `tstart::Real`: Starting time of the excitation [s]
  * `duration::Real`: Duration of the excitation [s]
  * `fc::Real`: Center frequency of the pulse [Hz]
  * `precision::Real`: Precision of the pulse (default = 4.)

**Note**

The precision parameter calibrates the standard deviation of the pulse, so that the duration = n x σ, within some precision. If n = 1.96 then the confidence interval of the Gaussian distribution is 95%. To do so, we compute n so that at t = duration = n x σ , the amplitude of F x exp(-0.5*(t - duration/2)^2/sigma^2) = 10^(-precision)
