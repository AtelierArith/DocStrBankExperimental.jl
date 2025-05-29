```
MuTunerLogger(n₀::T, β::T, V::Int, u₀::T=1.0, μ₀::T=0.0, c::T=0.5,
              s::S=zero(T)) where {T<:AbstractFloat, S<:Number}
```

Constructs an instance of [`MuTunerLogger`](@ref).

# Arguments

  * `n₀::T`: Target particle density $\langle n \rangle$.
  * `β::T`: Inverse temperature.
  * `V::Int`: System size.
  * `u₀::T=1.0`: Characteristic intensive energy scale.
  * `μ₀::T=0.0`: Initial guess for chemical potential.
  * `c::T=0.5`: Fraction of history to discard when calculating forgetful averages and variances.
  * `s::S=zero(T)`: An example of the sign, to determine whether the type of the sign if real or complex.
