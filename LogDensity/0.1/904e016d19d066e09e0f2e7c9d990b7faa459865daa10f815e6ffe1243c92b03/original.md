```
β = logdensityderivatives( X, x, h; various optional arguments )

Computes estimates of the derivatives of the log density of the data 
in the vector X evaluated at the elements in the vector x, using the 
bandwidth h. Returns a matrix β with rows corresponding to the 
evaluation points and columns to the derivatives.  This is a matrix
even if S = 1.
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
  * `anal::Bool=true`: whether to run many sanity checks
