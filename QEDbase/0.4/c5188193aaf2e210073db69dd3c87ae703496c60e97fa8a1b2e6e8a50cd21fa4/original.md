```
setMinus!(lv,value)
```

Sets the minus component of a `LorentzVectorLike` to a given `value`.

!!! note
    The `value` set with `setMinus!` is then returned by [`getMinus`](@ref). Since the minus component is computed on the call of `getMinus`, the setter `setMinus!` changes several components of the given `LorentzVectorLike`.

