```
setPlus!(lv,value)
```

Sets the plus component of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setPlus!` is then returned by [`getPlus`](@ref). Since the plus component is computed on the call of `getPlus`, the setter `setPlus!` changes several components of the given `LorentzVectorLike`.

