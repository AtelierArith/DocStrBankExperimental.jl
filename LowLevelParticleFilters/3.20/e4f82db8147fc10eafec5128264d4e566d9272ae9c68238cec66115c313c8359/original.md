```
RBParticle(xn, xl, R) <: AbstractVector
```

A struct that represents the state of a Rao-Blackwellized particle filter. The struct is an abstract vector, and when indexed like a vector it behaves as `[xn; xl]`. To access nonlinear or linear substate individually, access the fields `xn` and `xl`.

# Arguments:

  * `xn`: The nonlinear state vector
  * `xl`: The linear state vector
  * `R`: The covariance matrix for the linear state
