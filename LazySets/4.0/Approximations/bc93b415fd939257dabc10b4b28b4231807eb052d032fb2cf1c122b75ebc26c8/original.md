```
hausdorff_distance(X::LazySet{N}, Y::LazySet{N}; [p]::N=N(Inf),
                   [ε]=N(1e-3)) where {N}
```

Compute the Hausdorff distance between two convex sets up to a given threshold.

### Input

  * `X` – convex set
  * `Y` – convex set
  * `p` – (optional, default: `Inf`) norm parameter of the Hausdorff distance
  * `ε` – (optional, default: `1e-3`) precision threshold; the true Hausdorff        distance is allowed to diverge from the result by at most this value

### Output

A value from the $ε$-neighborhood of the Hausdorff distance between $X$ and $Y$.

### Notes

Given a $p$-norm, the Hausdorff distance $d_H^p(X, Y)$ between sets $X$ and $Y$ is defined as follows:

$$
    d_H^p(X, Y) = \inf\{δ ≥ 0 \mid Y ⊆ X ⊕ δ 𝐵_p^n \text{ and } X ⊆ Y ⊕ δ 𝐵_p^n\}
$$

Here $𝐵_p^n$ is the $n$-dimensional unit ball in the $p$-norm.

The implementation may internally rely on the support function of $X$ and $Y$; hence any imprecision in the implementation of the support function may affect the result. At the time of writing, the only convex set type with imprecise support function is the lazy [`Intersection`](@ref).

### Algorithm

We perform binary search for bounding the Hausdorff distance in an interval $[l, u]$, where initially $l$ is $0$ and $u$ is described below. The binary search terminates when $u - l ≤ ε$, i.e., the interval becomes sufficiently small.

To find an upper bound $u$, we start with the heuristics of taking the biggest distance in the axis-parallel directions. As long as this bound does not work, we increase the bound by $2$.

Given a value $δ$, to check whether the sets are within Hausdorff distance $δ$, we simply check the inclusions given above, where on the right-hand side we use a lazy `Bloating`.
