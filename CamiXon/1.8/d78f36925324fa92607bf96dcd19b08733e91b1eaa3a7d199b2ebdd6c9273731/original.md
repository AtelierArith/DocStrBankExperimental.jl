```
rotbarrier(grid::CamiDiff.Grid{T}; ℓ=0) where T<:Real
```

CamiDiff.Grid representation of rotational barrier potential in wavenumber notation,

$$
V_{rot}(r) = \frac{\ell(\ell+1)}{r^{2}},
$$

where ℓ is the rotational quantum number.
