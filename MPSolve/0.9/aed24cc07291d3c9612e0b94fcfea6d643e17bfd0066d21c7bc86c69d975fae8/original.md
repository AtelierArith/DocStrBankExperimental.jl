```
(approximations, radii) = mps_roots(coefficients, output_precision=53)
```

Approximate the roots of a polynomial specified by the array of its coefficients. Output precision is specified in bits.

# Example

```jldoctest
julia> N = 64;

julia> cfs = zeros(Int, N + 1); cfs[end] = -(cfs[1] = 1);

julia> (app, rad) = mps_roots(cfs, 100);

julia> all(map(x->abs((x^N - 1)/(N*x^(N - 1))), app) < rad)
true
```
