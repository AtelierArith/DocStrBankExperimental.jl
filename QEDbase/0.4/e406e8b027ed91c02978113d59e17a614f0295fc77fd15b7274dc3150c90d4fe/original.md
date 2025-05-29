```
setRho!(lv,value)
```

Sets the magnitude of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setRho!` is then returned by [`getRho`](@ref). Since the magnitude is computed on the call of `getRho`, the setter `setRho!` changes several components of the given `LorentzVectorLike`.

