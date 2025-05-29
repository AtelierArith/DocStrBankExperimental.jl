Type: OneDAtX

Methods: update!, reinit!, copy

A structure designed to track line search information from one iteration to another. Given f : ℜⁿ → ℜ, define h(θ) = f(x + θ*d) where x and d are vectors of same dimension and θ is a scalar, more specifically the step size.

Tracked data can include:

  * x             : the current step size
  * fx [opt]      : h(θ) at the current iteration
  * gx [opt]      : h'(θ)
  * f₀ [opt]      : h(0)
  * g₀ [opt]      : h'(0)
  * d [opt]       : search direction
  * res [opt]     : residual
  * current_time  : the time at which the line search algorithm started.
  * current_score : the score at which the line search algorithm started.

Constructors:  `OneDAtX(:: T, :: S; fx :: T = _init_field(T), gx :: T = _init_field(T), f₀ :: T = _init_field(T), g₀ :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <: Number}`

`OneDAtX(:: T; fx :: T = _init_field(T), gx :: T = _init_field(T), f₀ :: T = _init_field(T), g₀ :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: T = _init_field(T))  where T <: Number`

Note: 

  * By default, unknown entries are set using `_init_field`.
  * By default the type of `current_score` is `eltype(x)` and cannot be changed once the State is created.  To have a vectorized `current_score` of length n, use `OneDAtX(x, Array{eltype(x),1}(undef, n))`.
