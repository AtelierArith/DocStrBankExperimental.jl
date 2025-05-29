```
StateSpaceModalFreqProblem(css::ContinuousStateSpace, F, freq, So, n)
```

Structure containing the data feeding the modal solver for calculating the frequency response

**Fields**

  * `css`: Continuous-time state space model
  * `F`: External force matrix
  * `freq`: Frequencies of interest
  * `So`: Selection matrix for observation points
  * `n`: Number of modes to keep in the modal basis
