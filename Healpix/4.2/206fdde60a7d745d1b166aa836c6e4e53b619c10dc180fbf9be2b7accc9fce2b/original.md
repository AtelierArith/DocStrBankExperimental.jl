```
almExplicitIndex(lmax) -> Vector{Int}
almExplicitIndex(lmax, mmax) -> Vector{Int}
almExplicitIndex(alm::Alm{T}) where {T} -> Vector{Int}
```

Compute the explicit index scheme, i.e. $\mathrm{index} = \ell^2 + \ell + m + 1$ up to a certain $ℓ$ and $m$ if specified, or taken from the `Alm` passed. If not passed, `mmax` is defaulted to `lmax`. If `lmax` and `mmax` are inconsistent or negative, a `DomainError` exception is thrown.
