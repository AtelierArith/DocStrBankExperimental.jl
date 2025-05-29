```
empirical_sinkhorn(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}};
    reg::Union{PyObject,Float64} = 1.0, iter::Int64 = 1000, tol::Float64 = 1e-9, method::String="sinkhorn", dist::Function=dist, returnall::Bool=false)
```

Computes the empirical Sinkhorn distance with sinkhorn algorithm. Here $x$ and $y$ are samples from two distributions.  

  * `reg` (default = 1.0): entropy regularization parameter
  * `tol` (default = 1e-9), `iter` (default = 1000): tolerance and max iterations for the Sinkhorn algorithm
  * `dist` (default = 2): Integer or Function, the distance function between two samples; if `dist` is integer, $L-dist$ norm is used.
  * `returnall`: returns (`TransportMatrix`, `Loss`) if true; otherwise, only `Loss` is returned.

The implementation are adapted from https://github.com/rflamary/POT.  
