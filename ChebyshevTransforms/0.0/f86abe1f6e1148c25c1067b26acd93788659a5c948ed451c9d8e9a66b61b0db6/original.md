```
paduatransform!(coeffs, P::PaduaTransformPlan, vals[, lex])
```

obtain coefficients of Chebyshev polynomials on 2D via the Padua transform, given values `vals` evaluated at the Padua points. Coefficients will be written into `coeffs`, which should either be a matrix, a vector or an iterable of either.

If an iterable of `vals` vectors and a corresponding iterable of `coeffs` matrixes or vectors is given, each `vals` vector will be transformed seperately in a multidimensional Padua transform.

`lex` determines the order in which coefficients are written into `out` if `out` is a vector. See [`fromcoeffsmat!`](@ref) for details.

!!! warning
    if `coeffs` is a matrix, make sure that all entries in the lower right diagonal are zero as these will not get overwritten.


# Examples

```jldoctest
julia> plan = PaduaTransformPlan{Float64}(2);

julia> f(x, y) = 3 + 4x + 5 * x*y, 6 + 7y
f (generic function with 1 method)

julia> vals = getpaduapoints(f, 2)
6×2 Matrix{Float64}:
 12.0  13.0
  4.5   2.5
  3.0   9.5
  3.0  -1.0
 -6.0  13.0
  1.5   2.5

julia> paduatransform!(zeros(3, 3), plan, vals[:, 1])
3×3 Matrix{Float64}:
 3.0  4.0  0.0
 0.0  5.0  0.0
 0.0  0.0  0.0

julia> paduatransform!(zeros(6), plan, vals[:, 2], Val(true))
6-element Vector{Float64}:
 6.0
 0.0
 7.0
 0.0
 0.0
 0.0

julia> paduatransform!((zeros(3, 3), zeros(3, 3)), plan, vals)
([3.0 4.0 0.0; 0.0 5.0 0.0; 0.0 0.0 0.0], [6.0 0.0 0.0; 7.0 0.0 0.0; 0.0 0.0 0.0])
```
