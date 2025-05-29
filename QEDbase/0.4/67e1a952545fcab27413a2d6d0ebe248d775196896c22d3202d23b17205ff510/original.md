```
setCosTheta!(lv,value)
```

Sets the cosine of the theta angle of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setCosTheta!` is then returned by [`getCosTheta`](@ref). Since the cosine of the theta angle is computed on the call of `getCosTheta`, the setter `setCosTheta!` changes several components of the given `LorentzVectorLike`.

