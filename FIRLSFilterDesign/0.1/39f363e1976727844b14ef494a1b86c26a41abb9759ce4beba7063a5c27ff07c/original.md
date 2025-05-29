```
firls_design(filter_order::Integer, bands_DW::Matrix, D::Matrix, W::Matrix, antisymmetric::Bool; fs::Real = 1, solver::Function = \)
```

Designs a linear-phase FIR filter.

# Arguments

  * `filter_order::Integer`   : the order of the FIR filter.
  * `bands_DW::Matrix`        : a matrix of size (N,2) which contains rows of sequential frequency bands, spanning [0, fs/2].
  * `D::Matrix`               : a matrix of size (N,2) which contains rows of amplitude responses for the frequency bands in `bands_DW`. The first and second columns indicate the amplitude response at the lower and upper bound of the frequency bands, interpolated linearly in between.
  * `W::Matrix`               : a matrix of size (N,2) which contains rows of weighting coefficients for the frequency bands in `bands_DW`. The first and second columns indicate the weighting at the lower and upper bound of the frequency bands, interpolated linearly in between.
  * `antisymmetric::Bool`     : a Boolean that signifies whether the filter coefficients will be anti-symmetric, as used in type III and IV FIR filters.
  * `fs::Real`                : the sampling frequency.
  * `solver::Function`        : the function that is called to solve the equation $Qa = b$, with the function call: `solver(Q,b)` which returns `a`.

# Outputs

  * `h` : a vector of linear-phase FIR filter coefficients.
