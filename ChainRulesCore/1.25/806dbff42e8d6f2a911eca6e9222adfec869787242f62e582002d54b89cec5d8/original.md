```
add!!(x, t::InplacableThunk)
```

The specialization of `add!!` for [`InplaceableThunk`](@ref) promises to only call `t.add!` on `x` if `x` is suitably mutable; otherwise it will be out of place.
