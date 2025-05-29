```
propagate_root(dynamics::D, jd0::V, tspan::T, q0::Vector{U}, params::NEOParameters{T};
    kwargs...) where {T <: Real, U <: Number, V <: Number D}
```

Integrate an orbit via the Taylor method while finding the zeros of `NEOs.rvelea`.

## Arguments

  * `dynamics::D`: dynamical model function.
  * `jd0::V`: initial Julian date (TDB).
  * `tspan::T`: time span of the integration [in years].
  * `q0::Vector{U}`: vector of initial conditions.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).

## Keyword arguments

  * `eventorder::Int`: order of the derivative of `rvelea` whose roots are computed.
  * `newtoniter::Int`: maximum Newton-Raphson iterations per detected root.
  * `nrabstol::T`: allowed tolerance for the Newton-Raphson process.
