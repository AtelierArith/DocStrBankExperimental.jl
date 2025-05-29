```
ZNormalizer{T} <: AbstractNormalizer{T, 1}
```

Utility object that normalizes an input array on the fly. Works like a vector, index into window with `z[i]`, index into normalized window with `z[!,i]`.

# Arguments:

  * `x::Vector{T}`: The vecetor to operate on
  * `n::Int`: The lenght of a window
  * `μ::T`: mean over window
  * `σ::T`: std over window
  * `s::T`: sum over window
  * `ss::T`: sum^2 over window
  * `i::Int`: the current index
  * `buffer::Vector{T}`: stores calculated normalized values, do not access this, it might not be complete
  * `bufi::Int`: index of last normalized value
