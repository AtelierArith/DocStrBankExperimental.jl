```
ExponentialSmoothing(
    y::Vector{Fl}; 
    trend::Bool = false,
    damped_trend::Bool = false,
    seasonal::Int = 0
) where Fl
```

Linear exponential smoothing models. These models are also known as ETS in the literature. This model is estimated using the Kalman filter for linear Gaussian state space models, for this reason the possible models are the following ETS with additive errors:

  * ETS(A, N, N)
  * ETS(A, A, N)
  * ETS(A, Ad, N)
  * ETS(A, N, A)
  * ETS(A, A, A)
  * ETS(A, Ad, A)

Other softwares have use the augmented least squares approach and have all the possible ETS  combinations. The Kalman filter approach might be slower than others but have the advantages of filtering the components.

# References

  * Hyndman, Rob, Anne B. Koehler, J. Keith Ord, and Ralph D. Snyder. Forecasting with exponential smoothing: the state space approach. Springer Science & Business Media, 2008.
  * Hyndman, Robin John; Athanasopoulos, George.  Forecasting: Principles and Practice.  2nd ed. OTexts, 2018.
