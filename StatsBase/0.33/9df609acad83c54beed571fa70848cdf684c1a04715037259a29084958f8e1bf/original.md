```
eweights(t::AbstractVector{<:Integer}, λ::Real; scale=false)
eweights(t::AbstractVector{T}, r::StepRange{T}, λ::Real; scale=false) where T
eweights(n::Integer, λ::Real; scale=false)
```

Construct a [`Weights`](@ref) vector which assigns exponentially decreasing weights to past observations (larger integer values `i` in `t`). The integer value `n` represents the number of past observations to consider. `n` defaults to `maximum(t) - minimum(t) + 1` if only `t` is passed in and the elements are integers, and to `length(r)` if a superset range `r` is also passed in. If `n` is explicitly passed instead of `t`, `t` defaults to `1:n`.

If `scale` is `true` then for each element `i` in `t` the weight value is computed as:

$(1 - λ)^{n - i}$

If `scale` is `false` then each value is computed as:

$λ (1 - λ)^{1 - i}$

# Arguments

  * `t::AbstractVector`: temporal indices or timestamps
  * `r::StepRange`: a larger range to use when constructing weights from a subset of timestamps
  * `n::Integer`: the number of past events to consider
  * `λ::Real`: a smoothing factor or rate parameter such that $0 < λ ≤ 1$. As this value approaches 0, the resulting weights will be almost equal, while values closer to 1 will put greater weight on the tail elements of the vector.

# Keyword arguments

  * `scale::Bool`: Return the weights scaled to between 0 and 1 (default: false)

# Examples

```julia-repl
julia> eweights(1:10, 0.3; scale=true)
10-element Weights{Float64,Float64,Array{Float64,1}}:
 0.04035360699999998
 0.05764800999999997
 0.08235429999999996
 0.11764899999999996
 0.16806999999999994
 0.24009999999999995
 0.3429999999999999
 0.48999999999999994
 0.7
 1.0
```

# Links

  * https://en.wikipedia.org/wiki/Moving*average#Exponential*moving_average
  * https://en.wikipedia.org/wiki/Exponential_smoothing
