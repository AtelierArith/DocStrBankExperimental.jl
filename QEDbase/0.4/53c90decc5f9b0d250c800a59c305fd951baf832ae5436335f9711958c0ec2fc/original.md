```
setTransverseMass!(lv,value)
```

Sets the transverse mass of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setTransverseMass!` is then returned by [`getTransverseMass`](@ref). Since the transverse mass is computed on the call of `getTransverseMass`, the setter `setTransverseMass!` changes several components of the given `LorentzVectorLike`.

