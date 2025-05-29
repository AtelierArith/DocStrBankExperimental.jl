```
setRapidity!(lv,value)
```

Sets the rapidity of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setRapidity!` is then returned by [`getRapidity`](@ref). Since the rapidity is computed on the call of `setRapidity`, the setter `setRapidity!` changes several components of the given `LorentzVectorLike`.

