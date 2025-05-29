```
⊕(ir1::T, ir2::T, ir3::T...) where T<:AbstractIrrep --> T
```

Compute the representation obtained from direct sum of the irreps `ir1`, `ir2`, `ir3`, etc. The resulting representation is reducible and has dimension `irdim(ir1) + irdim(ir2) + irdim(ir3) + …`.

The groups of the provided irreps must be identical. If `T isa LGIrrep`, the irrep translation factors must also be identical (due to an implementation detail of the `LGIrrep` type).

Also provided via `Base.:+`.
