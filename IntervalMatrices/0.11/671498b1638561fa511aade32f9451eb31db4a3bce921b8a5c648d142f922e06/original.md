```
AffineIntervalMatrix1{T, IT, MT0<:AbstractMatrix{T}, MT1<:AbstractMatrix{T}} <: AbstractIntervalMatrix{IT}
```

Interval matrix representing the matrix

$$
A₀ + λA₁,
$$

where $A₀$ and $A₁$ are real (or complex) matrices, and $λ$ is an interval.

### Fields

  * `A0` – matrix
  * `A1` – matrix
  * `λ`  – interval

### Examples

The matrix $I + [1 1; -1 1] * interval(0, 1)$ is:

```jldoctest
julia> using LinearAlgebra

julia> P = AffineIntervalMatrix1(Matrix(1.0I, 2, 2), [1 1; -1 1.], interval(0, 1));

julia> P
2×2 AffineIntervalMatrix1{Float64, Interval{Float64}, Matrix{Float64}, Matrix{Float64}}:
  [1.0, 2.0]  [0.0, 1.0]
 [-1.0, 0.0]  [1.0, 2.0]
```
