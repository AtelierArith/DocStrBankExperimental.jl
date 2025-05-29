```
detect_new_linearities(rep::HRepresentation{T}, solver; verbose=0, tol=Base.rtoldefault(T)) where {T}
```

Given a polyhedron with H-representation `rep`, detect whether a new hyperplane can be generated from the halfspaces in `halfspaces` using an linear program solved by `solver`. The method is similar to the method used for lines described as follows. This function is automatically called by `removehredundancy` if a solver is provided.

```
detect_new_linearities(rep::VRepresentation{T}, solver; verbose=0, tol=Base.rtoldefault(T)) where {T}
```

Given a cone defined by the V-representation `rep` (ignoring the points in the representation if any), detect whether a new line can be generated from the rays in `rays` using an linear program solved by `solver`. The method is as follows (suppose `lines` is empty for simplicity). This function is automatically called by `removevredundancy` if a solver is provided.

The keyword argument `tol` is used as a tolerance to decide whether a number is zero.

If there was a line `l` in the cone, it would mean that there exist `μ >= 0` and `ν >= 0` such that `Σ μ_i r_i = l` and `Σ ν_i r_i = -l`. We deduce from this that `Σ λ_i r_i = 0` where `λ = μ + ν`.

Conversely, if there are `λ >= 0` such that `Σ λ_i r_i = 0` then let `j` be the index of `λ` with largest magnitude (to make sure it is nonzero). We have `Σ_{i != j} λ_i/λ_j r_i = -r_j`. As both `r_j` and `-r_j` are in the cone, `r_j` generates a line in the cone. However, this means that we now have `Σ_{i != j} λ_i/λ_j r_i ≡ 0 (mod r_j)` so if there is another `λ_i` with nonzero value, we can transform it to a line as well. In summary, we have a line `r_i` for each `i` such that `λ_i != 0`.

The dual program is:

```
max z
s.t. r_i'x ≥ z
```

When the primal is feasible, the dual program may still be feasible. We know that `z = 0` by strong duality as the objective value needs to be equal to the objective of the primal which is zero. So the constraints are `r_i'x ≥ 0`. If we have `r_i'x > 0` for some `i`, it means that `-r_i` does not belong to the cone hence `r_i` can be dropped for the purpose of searching for lines.

## Note

In CDDLib, the dual program is solved, if the objective value is zero then linearity are found by, for each `i` such that `r_i'x = 0`, solve an LP to find whether `-r_i` belongs to the cone. CDDLib ignores the primal results provided in `λ` which directly gives linearity without the need to solve an LP for each ray. The method implemented in Polyhedra is therefore significantly more efficient as its complexity is `O(dimension of linespace)` which is upper bounded by `O(fulldim)` while the method of CDDLib is `O(number of rays)`.
