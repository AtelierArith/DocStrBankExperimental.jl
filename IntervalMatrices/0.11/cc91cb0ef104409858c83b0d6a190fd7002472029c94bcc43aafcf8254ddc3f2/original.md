```
IntervalMatrixPower{T}
```

A wrapper for the matrix power that can be incremented.

### Fields

  * `M`  – the original matrix
  * `Mᵏ` – the current matrix power, i.e., $M^k$
  * `k`  – the current power index

### Notes

The wrapper should only be accessed using the interface functions. The internal representation (such as the fields) are subject to future changes.

### Examples

```jldoctest
julia> A = IntervalMatrix([interval(2, 2) interval(2, 3); interval(0, 0) interval(-1, 1)])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [2.0, 2.0]   [2.0, 3.0]
 [0.0, 0.0]  [-1.0, 1.0]

julia> pow = IntervalMatrixPower(A);

julia> increment!(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [4.0, 4.0]  [2.0, 9.0]
 [0.0, 0.0]  [0.0, 1.0]

julia> increment(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [8.0, 8.0]  [-1.0, 21.0]
 [0.0, 0.0]  [-1.0, 1.0]

julia> matrix(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [4.0, 4.0]  [2.0, 9.0]
 [0.0, 0.0]  [0.0, 1.0]

julia> index(pow)
2

julia> base(pow)
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [2.0, 2.0]   [2.0, 3.0]
 [0.0, 0.0]  [-1.0, 1.0]

```
