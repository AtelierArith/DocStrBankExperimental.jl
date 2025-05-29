```
Symmetric(g)
```

Wraps a single-sided output function `g` turns it into a double sided output function which applies

```
y_dst = g(...)
y_src = y_dst
```

`g` can be a `Number`/`AbstractArray` to impicitly wrap the corresponding [`StateMask`](@ref).

See also [`AntiSymmetric`](@ref), [`Directed`](@ref), [`Fiducial`](@ref) and [`StateMask`](@ref).
