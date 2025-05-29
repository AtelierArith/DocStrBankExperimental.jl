```
AntiSymmetric(g_dst)
```

Wraps a single-sided output function `g_dst` turns it into a double sided output function which applies

```
y_dst = g_dst(...)
y_src = -y_dst
```

`g_dst` can be a `Number`/`AbstractArray` to impicitly wrap the corresponding [`StateMask`](@ref).

See also [`Symmetric`](@ref), [`Directed`](@ref), [`Fiducial`](@ref) and [`StateMask`](@ref).
