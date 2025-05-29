```
±(C::MT, S::MT) where {T, MT<:AbstractMatrix{T}}
```

Return an interval matrix such that the center and radius of the intervals is given by the matrices `C` and `S` respectively.

### Input

  * `C` – center matrix
  * `S` – radii matrix

### Output

An interval matrix `M` such that `M[i, j]` corresponds to the interval whose center is `C[i, j]` and whose radius is `S[i, j]`, for each `i` and `j`. That is, $M = C + [-S, S]$.

### Notes

The radii matrix should be nonnegative, i.e. `S[i, j] ≥ 0` for each `i` and `j`.

### Examples

```jldoctest
julia> [1 2; 3 4] ± [1 2; 4 5]
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
  [0.0, 2.0]   [0.0, 4.0]
 [-1.0, 7.0]  [-1.0, 9.0]
```
