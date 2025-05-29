```
StateSpacemodalFRFProblem(css::ContinuousStateSpace, freq, type, So, Se, n)
```

Structure containing the data feeding the direct solver for calculating an FRF

**Fields**

  * `css`: Continuous-time state space model
  * `freq`: Frequencies of interest
  * `So`: Selection matrix for observation points
  * `Se`: Selection matrix for excitation points
  * `n`: Number of modes to keep in the modal basis
