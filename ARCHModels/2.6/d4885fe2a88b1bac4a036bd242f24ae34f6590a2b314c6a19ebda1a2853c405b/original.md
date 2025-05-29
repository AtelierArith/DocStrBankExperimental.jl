```
fit(DCCspec::Type{<:DCC{p, q, VS<:UnivariateVolatilitySpec}}, data::Matrix;
    method=:largescale,  dist=MultivariateStdNormal, meanspec=Intercept,
    algorithm=BFGS(), autodiff=:forward, kwargs...)
```

Fit the DCC model specified by `DCCspec` to `data`. If `p` and `q` or `VS` are unspecified, then these default to 1, 1, and `GARCH{1, 1}`.

# Keyword arguments:

  * `method`: one of `:largescale` or `twostep`
  * `dist`: the error distribution.
  * `meanspec`: the mean specification, as a type.
  * `algorithm, autodiff, kwargs, ...`: passed on to the optimizer.

# Example: DCC{1, 1, GARCH{1, 1}} model:

```jldoctest
julia> fit(DCC, DOW29)

29-dimensional DCC{1, 1} - GARCH{1, 1} - Intercept{Float64} specification, T=2785.

DCC parameters, estimated by largescale procedure:
────────────────────
       β₁         α₁
────────────────────
  0.88762  0.0568001
────────────────────

Calculating standard errors is expensive. To show them, use
`show(IOContext(stdout, :se=>true), <model>)`
```
