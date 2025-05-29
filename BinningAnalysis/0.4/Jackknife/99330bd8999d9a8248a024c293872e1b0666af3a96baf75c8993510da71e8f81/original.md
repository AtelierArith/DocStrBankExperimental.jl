```
jackknife(g::Function, a[, b, ...])
```

Returns the jackknife estimate and error for a given function `g(<a>, <b>, ...)` acting on the means of the samples `a`, `b`, etc.

Example:     # Assuming some sample xs is given     # variance of sample xs     g(x2, x) = x2 - x^2     error = jackknife(g, xs.^2, xs)

See also: [`estimate`](@ref), [`std_error`](@ref)
