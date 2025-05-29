```
AffineIntervalMatrix{T, IT, MT0<:AbstractMatrix{T}, MT<:AbstractMatrix{T}, MTA<:AbstractVector{MT}} <: AbstractIntervalMatrix{IT}
```

Interval matrix representing the matrix

$$
A₀ + λ₁A₁ + λ₂A₂ + … + λₖAₖ,
$$

where $A₀$ and $A₁, …, Aₖ$ are real (or complex) matrices, and $λ₁, …, λₖ$ are intervals.

### Fields

  * `A0` – matrix
  * `A`  – vector of matrices
  * `λ`  – vector of intervals

### Notes

This type is the general case of the [`AffineIntervalMatrix1`](@ref), which only contains one matrix proportional to an interval.

### Examples

The affine matrix $I + [1 1; -1 1] * interval(0, 1) + [0 1; 1 0] * interval(2, 3)$ is:

```jldoctest
julia> using LinearAlgebra

julia> A0 = Matrix(1.0I, 2, 2);

julia> A1 = [1 1; -1 1.]; A2 = [0 1; 1 0];

julia> λ1 = interval(0, 1); λ2 = interval(2, 3);

julia> P = AffineIntervalMatrix(A0, [A1, A2], [λ1, λ2])
2×2 AffineIntervalMatrix{Float64, Interval{Float64}, Matrix{Float64}, Matrix{Float64}, Vector{Matrix{Float64}}, Vector{Interval{Float64}}}:
 [1.0, 2.0]  [2.0, 4.0]
 [1.0, 3.0]  [1.0, 2.0]
```
