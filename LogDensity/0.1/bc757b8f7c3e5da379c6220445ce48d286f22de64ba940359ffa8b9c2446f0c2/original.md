```
(logf, β) = logdensity( X, x, h; various optional arguments )

Computes estimates of the log density and its derivatives of the data 
in the vector X evaluated at the elements in the vector x, using the 
bandwidth h. Returns a tuple ( logf, β ) where logf is a vector whose
elements correspond to the evaluation points and β a matrix with rows 
corresponding to the evaluation points and columns to the derivatives;  
this is a matrix even if S = 1.
```

# Mandatory arguments

  * `X::Vector{T}`: vector of data
  * `x::Vector{T}`: vector of evaluation points
  * `h::T`: bandwidth

T is a floating point type

# Optional arguments

  * `g::Function=g`: the function g to be used (see Pinkse and Schurter)
  * `dg::Function=dg`: its derivative
  * `S::Int=1`: the number of derivatives to be computed
  * `minx::T=0.0`: the left hand side of the support
  * `maxx::T=Inf`: the right hand side of the support
  * `logf::Bool=true`: whether the log density itself should be computed
  * `mz::Function=LogDensity.epanechnikov`: the kernel to be used for the log density itself
  * `anal::Bool=true`: whether to run many sanity checks

Other choices for the kernel are:  LogDensity.quartic LogDensity.gaussian LogDensity.triweight LogDensity.uniform LogDensity.cosinus
