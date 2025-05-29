```
mJy_to_W(S::Union{Real, Unitful.AbstractQuantity}, h::AbstractGadgetHeader)
```

Converts synchrotron flux density `S` in `[mJy]` to `[W/Hz]` for a given redshift and cosmology taken from `AbstractGadgetHeader`.
