```
project(M::Rotations, p; check_det = true)
```

Project `p` to the nearest point on manifold `M`.

Given the singular value decomposition $p = U Σ V^\mathrm{T}$, with the singular values sorted in descending order, the projection is

$$
\operatorname{proj}_{\mathrm{SO}(n)}(p) =
U\operatorname{diag}\left[1,1,…,\det(U V^\mathrm{T})\right] V^\mathrm{T}
$$

The diagonal matrix ensures that the determinant of the result is $+1$. If `p` is expected to be almost special orthogonal, then you may avoid this check with `check_det = false`.
