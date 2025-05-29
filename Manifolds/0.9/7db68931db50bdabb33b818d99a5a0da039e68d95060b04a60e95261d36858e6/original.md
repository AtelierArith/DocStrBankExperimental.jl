```
project(G::SpecialUnitary, p)
```

Project `p` to the nearest point on the [`SpecialUnitary`](@ref) group `G`.

Given the singular value decomposition $p = U S V^\mathrm{H}$, with the singular values sorted in descending order, the projection is

$$
\operatorname{proj}_{\mathrm{SU}(n)}(p) =
U\operatorname{diag}\left[1,1,…,\det(U V^\mathrm{H})\right] V^\mathrm{H}.
$$

The diagonal matrix ensures that the determinant of the result is $+1$.
