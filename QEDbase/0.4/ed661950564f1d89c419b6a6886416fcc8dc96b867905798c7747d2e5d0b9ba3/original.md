```
setPhi!(lv,value)
```

Sets the phi angle of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setPhi!` is then returned by [`getPhi`](@ref). Since the phi angle is computed on the call of `getPhi`, the setter `setPhi!` changes several components of the given `LorentzVectorLike`.

