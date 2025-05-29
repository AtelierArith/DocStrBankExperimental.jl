```
StateSpaceFRFProblem(css::ContinuousStateSpace, freq, type, So, Se)
```

Structure containing the data feeding the direct solver for calculating an FRF

**Fields**

  * `css`: Continuous-time state space model
  * `freq`: Frequencies of interest
  * `So`: Selection matrix for observation points
  * `Se`: Selection matrix for excitation points

**Note** It is assumed that the output equation is of the form y = So*x
