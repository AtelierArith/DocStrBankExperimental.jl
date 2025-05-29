```
minkowski_difference(P::LazySet, Q::LazySet)
```

Concrete Minkowski difference (geometric difference) of a polytopic set and a compact set.

### Input

  * `P` – polytopic set
  * `Q` – compact set that is subtracted from `P`

### Output

An `HPolytope` that corresponds to the Minkowski difference of `P` minus `Q` if `P` is bounded, and an `HPolyhedron` if `P` is unbounded.

### Notes

This implementation requires that the set `P` is polyhedral and that the set `Q` is bounded.

### Algorithm

This method implements [KolmanovskyG98; Theorem 2.3](@citet):

Suppose $P$ is a polyhedron

$$
P = \{z ∈ ℝ^n: sᵢᵀz ≤ rᵢ,~i = 1, …, k\}.
$$

where $sᵢ ∈ ℝ^n, sᵢ ≠ 0$, and $rᵢ ∈ ℝ$. Assume $ρ(sᵢ,Q)$ is defined for $i = 1, …, k$. Then the Minkowski difference is

$$
\{z ∈ ℝ^n: sᵢᵀz ≤ rᵢ - ρ(sᵢ,Q),~i = 1, …, k\}.
$$

While the algorithm applies the support function to `Q`, we have that $P ⊖ Q = P ⊖ \text{CH}(Q)$ whenever `P` is convex, where CH denotes the convex hull. Hence, if `Q` is not convex by type information, we wrap it in a lazy `ConvexHull`.
