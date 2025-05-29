```
polyhedral(F::Union{System, AbstractSystem};
    only_non_zero = false,
    endgame_options = EndgameOptions(),
    tracker_options = TrackerOptions())
```

Solve the system `F` in two steps: first solve a generic system derived from the support of `F` using a polyhedral homotopy as proposed in [^HS95], then perform a coefficient-parameter homotopy towards `F`. This returns a path tracker ([`PolyhedralTracker`](@ref) or [`OverdeterminedTracker`](@ref)) and an iterator to compute the start solutions.

If `only_non_zero` is true, then the algorithm will set up a start system that tracks fewer paths compared to `only_non_zero = false`.  In this case the number of paths to track is equal to the mixed volume of the Newton polytopes of `F`.  The computed solutions will include all solutions with non-zero coordinates.

If `only_non_zero` is `false`, then all isolated solutions of `F` are computed. In this case the number of paths to track is equal to the mixed volume of the convex hulls of $supp(F_i) ∪ \{0\}$ where $supp(F_i)$ is the support of $F_i$. See also [^LW96].

```
function polyhedral(
    support::AbstractVector{<:AbstractMatrix},
    coefficientss::AbstractVector{<:AbstractVector{<:Number}};
    kwargs...,
)
```

It is also possible to provide directly the support and coefficients of the system `F` to be solved.

[^HS95]: Birkett Huber and Bernd Sturmfels. “A Polyhedral Method for Solving Sparse Polynomial Systems.” Mathematics of Computation, vol. 64, no. 212, 1995, pp. 1541–1555

[^LW96]: T.Y. Li and Xiaoshen Wang. "The BKK root count in C^n". Math. Comput. 65, 216 (October 1996), 1477–1484.

### Example

We consider a system `f` which has in total 6 isolated solutions, but only 3 where all coordinates are non-zero.

```julia
@var x y
f = System([2y + 3 * y^2 - x * y^3, x + 4 * x^2 - 2 * x^3 * y])
tracker, starts = polyhedral(f; only_non_zero = false)
# length(starts) == 8
count(is_success, track.(tracker, starts)) # 6

tracker, starts = polyhedral(f; only_non_zero = true)
# length(starts) == 3
count(is_success, track.(tracker, starts)) # 3
```
