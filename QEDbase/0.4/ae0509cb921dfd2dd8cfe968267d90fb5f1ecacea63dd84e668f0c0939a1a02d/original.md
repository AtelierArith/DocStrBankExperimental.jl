```
setTheta!(lv,value)
```

Sets the theta angle of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setTheta!` is then returned by [`getTheta`](@ref). Since the theta angle is computed on the call of `getTheta`, the setter `setTheta!` changes several components of the given `LorentzVectorLike`.

