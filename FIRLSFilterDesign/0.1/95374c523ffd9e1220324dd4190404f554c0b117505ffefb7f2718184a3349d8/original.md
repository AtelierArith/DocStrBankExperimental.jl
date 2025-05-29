```
firls_design(filter_order::Integer, knotpoints_D::Vector, D::Vector, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

# Arguments

  * `filter_order::Integer`   : the order of the FIR filter.
  * `knotpoints_D::Vector`    : a vector of size `(N,)` which contains frequency knotpoints, spanning [0, fs/2].
  * `D::Vector`               : a vector of size `(N,)` which contains amplitude response values for the frequency knotpoints in `knotpoints_D::Vector`.
  * `antisymmetric::Bool`     : a Boolean that signifies whether the filter coefficients will be anti-symmetric, as used in type III and IV FIR filters.
  * `fs::Real`                : the sampling frequency.
  * `solver::Function`        : the function that is called to solve the equation $Qa = b$, with the function call: `solver(Q,b)` which returns `a`.

# Outputs

  * `h` : a vector of linear-phase FIR filter coefficients.
