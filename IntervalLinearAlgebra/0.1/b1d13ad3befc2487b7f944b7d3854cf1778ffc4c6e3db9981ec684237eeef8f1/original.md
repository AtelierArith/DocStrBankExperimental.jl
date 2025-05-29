```
GaussSeidel <: AbstractIterativeSolver
```

Type for the Gauss-Seidel solver of the interval linear system $Ax=b$. For details see Section 5.7.4 of [[HOR19]](@ref)

### Fields

  * `max_iterations` – maximum number of iterations (default 20)
  * `atol`           – absolute tolerance (default 0), if at some point $|xₖ - xₖ₊₁| < atol$                     (elementwise), then stop and return $xₖ₊₁$.                     If `atol=0`, then `min(diam(A))*1e-5` is used.

### Notes

  * An object of type `GaussSeidel` is a function with method

    ```
      (gs::GaussSeidel)(A::AbstractMatrix{T},
                        b::AbstractVector{T},
                        [x]::AbstractVector{T}=enclose(A, b)) where {T<:Interval}
    ```

    #### Input

      * `A`   – N×N interval matrix
      * `b`   – interval vector of length N
      * `x`   – (optional) initial enclosure for the solution of $Ax = b$. If not given,          it is automatically computed using [`enclose`](@ref enclose)

### Examples

```jldoctest
julia> A = [2..4 -1..1;-1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> b = [-2..2, -1..1]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-1, 1]

julia> gs = GaussSeidel()
GaussSeidel linear solver
max_iterations = 20
atol = 0.0

julia> gs(A, b)
2-element Vector{Interval{Float64}}:
 [-1.66668, 1.66668]
 [-1.33334, 1.33334]
```
