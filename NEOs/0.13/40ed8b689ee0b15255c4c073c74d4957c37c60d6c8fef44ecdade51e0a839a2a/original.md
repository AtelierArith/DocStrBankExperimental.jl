```
NEOParameters([params::NEOParameters{T};] kwargs...) where {T <: Real}
```

Parameters for all orbit determination functions.

## Propagation Parameters

  * `maxsteps::Int`: maximum number of steps for the integration (default: `500`).
  * `μ_ast::Vector{T}`: vector of gravitational parameters   (default: `μ_ast343_DE430[1:end]`).
  * `order::Int`: order of Taylor expansions wrt time (default: 25).
  * `abstol::T`: absolute tolerance used to compute propagation timestep   (default: `1e-20`).
  * `parse_eqs::Bool`: whether to use the specialized method of `jetcoeffs` or not   (default: `true`).
  * `bwdoffset/fwdoffset::T`: days to propagate beyond first (bwd) / last (fwd) observation   (default: `0.5`).
  * `coeffstol::T`: maximum size of the coefficients (default: `10.0`).

## Gauss Method Parameters

  * `safegauss::Bool`: whether to try Gauss Method only when exactly three tracklets   are available (default: `true`).
  * `refscale::Symbol`: horizontal scale for ADAM refinement of Gauss preliminary   orbit (default: `:log`).
  * `gaussorder::Int`: order of the jet transport perturbation (default: `6`).

## Too Short Arc Parameters

  * `H_max::T`: maximum absolute magnitude (default: `34.5`).
  * `a_max::T`: maximum semimajor axis (default: `100.0`).
  * `adamiter::Int`: maximum number of iterations for `ADAM` optimizer (default: `200`).
  * `adammode::Bool`: whether to perform ADAM iterations with all the observations   (default: `true`).
  * `adamQtol::T`: target function relative tolerance (default: `0.001`).
  * `tsaorder::Int`: order of the jet transport perturbation (default: `6`).

## Jet Transport Least Squares Parameters

  * `lsiter::Int`: maximum number of iterations for `leastsquares` (default: `5`).
  * `jtlsiter::Int`: maximum number of iterations for `jtls` (default: `5`).
  * `jtlsorder::Int`: order of the jet transport perturbation in `jtls` (default: `6`).
  * `significance::T`: chi-square significance level (default: `0.99`).
  * `jtlsmask::Bool`: whether to use `isjtlsfit` to skip bad-conditioned   preliminary orbits in `jtls` (default: `true`).

## Outlier Rejection Parameters

  * `outrej::Bool`: whether to perform outlier rejection during least squares   iterations (default: `false`).
  * `χ2_rec::T`: recovery threshold (default: `7.0`).
  * `χ2_rej::T`: rejection threshold (default: `8.0`).
  * `fudge::T`: rejection fudge term coefficient (default: `400.0`).
  * `max_per::T`: maximum allowed rejection percentage (default: `10.0`).
