```
GpBasisFnsζα(fns1::GpBasisFnsζ, fns2::GpBasisFnsζ)
```

2-D basis functions $N(ζ^α)$ at a single Gauss point $ζ^α$, as set by 1-D [`GpBasisFnsζ`](@ref) `fns1` and `fns2`.

Here $ζ^1$ and $ζ^2$ respectively correspond to the `ζ` values passed to `fns1` and `fns2`, even though this information is not stored. The 2-D basis functions are calculated as the tensor product of 1-D functions. The struct contains four fields:

  * `w` –> Gauss point weight, given by `fns1.w × fns2.w`
  * `N` –> `NEN`×1 vector of nonzero basis functions $N(ζ^α)$, ordered by the tensor product structure
  * `∂Nα` –> `NEN`×2 matrix of first derivatives: rows respectively contain $N_{, 1}$ and $N_{, 2}$
  * `∂∂Nαβ` –> `NEN`×3 matrix of second derivatives: rows respectively contain $N_{, 1 1}$, $N_{, 2 2}$, and $N_{, 1 2}$
