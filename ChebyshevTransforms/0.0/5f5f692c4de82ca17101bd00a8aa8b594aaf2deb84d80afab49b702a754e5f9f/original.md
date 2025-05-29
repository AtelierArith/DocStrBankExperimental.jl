```
invpaduatransform!(vals::AbstractVector, IP::InvPaduaTransformPlan, coeffs::AbstractMatrix)
```

evaluates the polynomial defined by the coefficients of Chebyshev polynomials `coeffs` on the Padua points using the inverse transform plan `IP` and writes the resulting values into `vals`.

If an iterable of `vals` vectors or a `vals` matrix and a corresponding iterable of `coeffs` matrixes is given, each `coeffs` matrix will be transformed seperately.

# Examples

```jldoctest
julia> iplan = InvPaduaTransformPlan{Float64}(2);

julia> coeffs = [[3 4 0; 0 5 0; 0 0 0], [3 0 1; 4 0 0; 0 0 0]]
2-element Vector{Matrix{Int64}}:
 [3 4 0; 0 5 0; 0 0 0]
 [3 0 1; 4 0 0; 0 0 0]

julia> invpaduatransform!(zeros(6), iplan, coeffs[1])
6-element Vector{Float64}:
 12.0
  4.5
  3.0
  3.0
 -6.0
  1.5

julia> invpaduatransform!((zeros(6), zeros(6)), iplan, coeffs)
([12.0, 4.5, 3.0, 3.0, -6.0, 1.5], [8.0, 2.0, 4.0, -2.0, 8.0, 2.0])

julia> invpaduatransform!(zeros(6, 2), iplan, coeffs)
6×2 Matrix{Float64}:
 12.0   8.0
  4.5   2.0
  3.0   4.0
  3.0  -2.0
 -6.0   8.0
  1.5   2.0

julia> getpaduapoints(2) do x, y; (3 + 4x + 5 * x*y, 3 + 2x^2 - 1 + 4y); end
6×2 Matrix{Float64}:
 12.0   8.0
  4.5   2.0
  3.0   4.0
  3.0  -2.0
 -6.0   8.0
  1.5   2.0
```
