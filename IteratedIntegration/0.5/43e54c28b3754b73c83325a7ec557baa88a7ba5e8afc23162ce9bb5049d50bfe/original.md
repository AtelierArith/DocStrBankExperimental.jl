```
nested_quad(f, a, b; kwargs...)
nested_quad(f, l::AbstractIteratedLimits{d,T}; routine=quadgk, kwargs...) where {d,T}
```

Calls `QuadGK` to perform iterated 1D integration of `f` over a compact domain parametrized by `AbstractIteratedLimits` `l`. In the case two points `a` and `b` are passed, the integration region becomes the hypercube with those extremal vertices (which mimics `hcubature`).

Returns a tuple `(I, E)` of the estimated integral and estimated error.

Keyword options include a relative error tolerance `rtol` (if `atol==0`, defaults to `sqrt(eps)` in the precision of the norm of the return type), an absolute error tolerance `atol` (defaults to 0), a maximum number of function evaluations `maxevals` for each nested integral (defaults to `10^7`), and the `order` of the integration rule (defaults to 7).

The algorithm is an adaptive Gauss-Kronrod integration technique: the integral in each interval is estimated using a Kronrod rule (`2*order+1` points) and the error is estimated using an embedded Gauss rule (`order` points). The interval with the largest error is then subdivided into two intervals and the process is repeated until the desired error tolerance is achieved. This 1D procedure is applied recursively to each variable of integration in an order determined by `l` to obtain the multi-dimensional integral.
