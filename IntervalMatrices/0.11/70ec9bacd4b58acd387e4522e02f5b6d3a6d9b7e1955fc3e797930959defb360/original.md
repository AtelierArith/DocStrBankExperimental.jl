```
IntervalMatrix(A::MT, B::MT) where {T, MT<:AbstractMatrix{T}}
```

Return an interval matrix such that the lower and upper bounds of the intervals are given by the matrices `A` and `B` respectively.

### Input

  * `A` – lower bound matrix
  * `B` – upper bound matrix

### Output

An interval matrix `M` such that `M[i, j]` corresponds to the interval whose lower bound is `A[i, j]` and whose upper bound is `B[i, j]`, for each `i` and `j`. That is, $M_{ij} = [A_{ij}, B_{ij}]$.

### Notes

The upper bound should be bigger or equal than the lower bound, i.e. `B[i, j] ≥ A[i, j]` for each `i` and `j`.

### Examples

```jldoctest
julia> IntervalMatrix([1 2; 3 4], [1 2; 4 5])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [1.0, 1.0]  [2.0, 2.0]
 [3.0, 4.0]  [4.0, 5.0]
```
