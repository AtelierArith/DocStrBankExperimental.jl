```
mJy_to_W( c::Cosmology.AbstractCosmology, S::Unitful.AbstractQuantity, z::Real )
```

Converts synchrotron flux density `S` in `[mJy]` to `[W/Hz]` for a given redshift `z` and cosmology `c`. Conserves unit information.
