```
dpss_tapers(n,w,k,tap_or_egval)
```

Simply compute discrete prolate spheroidal sequence tapers, eigenvalues 

...

# Arguments

  * `n::Int64`: Length of the taper
  * `nw::Float64`: Time-bandwidth product
  * `k::Int64`: Number of tapers
  * `tap_or_egval::Symbol = :tap`: Either :tap, :egval, or :both

...

...

# Outputs

  * `vv::Vector{Float64}`: The matrix of eigenvalues, if tap*or*egval is set to :tap
  * `dpss_eigval`: Struct conaining the dpss tapers

...
