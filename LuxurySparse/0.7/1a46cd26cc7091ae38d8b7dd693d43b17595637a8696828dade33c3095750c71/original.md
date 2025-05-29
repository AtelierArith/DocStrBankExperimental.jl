```
PermMatrix{Tv, Ti}(perm::AbstractVector{Ti}, vals::AbstractVector{Tv}) where {Tv, Ti<:Integer}
PermMatrix(perm::Vector{Ti}, vals::Vector{Tv}) where {Tv, Ti}
PermMatrix(ds::AbstractMatrix)
```

PermMatrix represents a special kind of linear operator: Permute and Multiply, which means `M * v = v[perm] * val` Optimized implementations of `inv` and `*` make it much faster than `SparseMatrixCSC`.

  * `perm` is the permutation order,
  * `vals` is the multiplication factor.

[Generalized Permutation Matrix](https://en.wikipedia.org/wiki/Generalized_permutation_matrix)

# Example

```julia-repl
julia> PermMatrix([2,1,4,3], rand(4))
4×4 SDPermMatrix{Float64, Int64, Vector{Float64}, Vector{Int64}}:
 0.0       0.182251  0.0      0.0
 0.887485  0.0       0.0      0.0
 0.0       0.0       0.0      0.182831
 0.0       0.0       0.22895  0.0

```
