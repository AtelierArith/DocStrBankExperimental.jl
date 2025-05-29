```
loggamma(a,x)
```

Returns the log of the upper incomplete gamma function [`gamma(a,x)`](@ref):

$$
\log \Gamma(a,x) = \log \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

supporting arbitrary real or complex `a` and `x`.

If `a` and/or `x` is complex, then `exp(loggamma(a,x))` matches `gamma(a,x)` (up to floating-point error), but `loggamma(a,x)` may differ from `log(gamma(a,x))` by an integer multiple of $2\pi i$ (i.e. it may employ a different branch cut).

See also [`loggamma(x)`](@ref).
