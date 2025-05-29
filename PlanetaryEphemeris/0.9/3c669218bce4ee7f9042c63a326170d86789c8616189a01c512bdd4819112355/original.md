```
propagate(maxsteps::Int, jd0::T, tspan::T; dynamics::Function = NBP_pN_A_J23E_J23M_J2S_threads!,
          nast::Int = 343, order::Int = order, abstol::T = abstol, parse_eqs::Bool = true) where {T <: Real}
```

Integrate the Solar System via the Taylor method.

# Arguments

  * `maxsteps::Int`: maximum number of steps for the integration.
  * `jd0::T`: initial Julian date.
  * `tspan::T`: time span of the integration (in Julian days).
  * `dynamics::Function`: dynamical model function.
  * `nast::Int`: number of asteroids to be considered in the integration.
  * `order::Int`: order of the Taylor expansions to be used in the integration.
  * `abstol::T`: absolute tolerance.
  * `parse_eqs::Bool`: whether to use the specialized method of `jetcoeffs!` (`true`) created with `@taylorize` or not.
