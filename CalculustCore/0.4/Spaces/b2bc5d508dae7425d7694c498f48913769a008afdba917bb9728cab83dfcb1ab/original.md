```
truncationOp(V::AbstractSpace{T, D} , fracs::NTuple{D}) where{T, D}
```

Truncation operator removes high-frequency modes in an input vector. `fracs[d]` is the proprtion of the spectrum to be preserved in `d`th dimension. In spectral space, the operator corresponds to diagonal scaling, where the first `fracs[d]` of the spectrum (low frequency modes) is multiplied by unity, and the remainder (high-frequency modes) with zeros.
