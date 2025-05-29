```
retract(M::AbstractManifold, p, X, method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)))
retract!(M::AbstractManifold, q, p, X, method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)))
```

Compute a retraction, an approximate version of the [`exp`](@ref)onential map, from `p` into direction `X`, scaled by `t`, on the [`AbstractManifold`](@ref) `M`. This can be computed in-place of `q`.

A retraction $\operatorname{retr}_p: T_p\mathcal M → \mathcal M$ is a smooth map that fulfils

1. $\operatorname{retr}_p(0) = p$
2. $D\operatorname{retr}_p(0): T_p\mathcal M → T_p\mathcal M$ is the identity map,

i.e. $D\operatorname{retr}_p(0)[X]=X$ holds for all $X∈ T_p\mathcal M$,

where $D\operatorname{retr}_p$ denotes the differential of the retraction

The retraction is called of second order if for all $X$ the curves $c(t) = R_p(tX)$ have a zero acceleration at $t=0$, i.e. $c''(0) = 0$.

Retraction method can be specified by the last argument, defaulting to [`default_retraction_method`](@ref)`(M)`. For further available retractions see the documentation of respective manifolds.

Locally, the retraction is invertible. For the inverse operation, see [`inverse_retract`](@ref).
