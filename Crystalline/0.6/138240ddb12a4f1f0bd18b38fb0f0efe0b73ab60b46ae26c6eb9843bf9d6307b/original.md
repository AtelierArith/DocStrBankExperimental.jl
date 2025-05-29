```
realify(lgirs::AbstractVector{<:LGIrrep}; verbose::Bool=false)
                                                    --> AbstractVector{<:LGIrrep}
```

From `lgirs`, a vector of `LGIrrep`s, determine the associated (gray) co-representations, i.e. the "real", or "physical" irreps that are relevant in scenarios with time-reversal symmetry.

For `LGIrrep` that are `REAL`, or that characterize a k-point 𝐤 which is not equivalent to -𝐤 (i.e. its star does not include both 𝐤 and -𝐤; equivalently, the little group includes time-reversal symmetry), the associated co-representations are just the  original irreps themselves.  For `PSEUDOREAL` and `COMPLEX` `LGIrrep`s where ±𝐤 are equivalent, the associated co-representations are built from pairs of irreps that "stick" together. This method computes this pairing and sets the `LGIrrep` field `iscorep` to true, to indicate that the resulting "paired irrep" (i.e. the co-representation) should be doubled with  itself (`PSEUDOREAL` reality) or its complex conjugate (`COMPLEX` reality).

### Background

For background, see p. 650-652 (and p. 622-626 for point groups) in Bradley & Cracknell's book. Their discussion is for magnetic groups (the "realified" irreps are, in fact, simply co-representations of the "gray" magnetic groups).  Cornwell's book also explicates this at some length as does Inui et al. (p. 296-299).

### Keyword arguments

  * `verbose::Bool`: if set to `true`, prints details about mapping from small irrep to small

corep for each `LGIrrep` (default: `false`).
