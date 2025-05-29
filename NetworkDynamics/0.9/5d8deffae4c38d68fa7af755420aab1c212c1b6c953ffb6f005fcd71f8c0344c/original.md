```
Fiducial(g_src, g_dst)
```

Wraps two single-sided output function `g_src` and `g_dst` and turns them into a double sided output function which applies

```
y_dst = g_src(...)
y_src = g_dst(...)
```

`g` can be a `Number`/`AbstractArray` to impicitly wrap the corresponding [`StateMask`](@ref).

See also [`AntiSymmetric`](@ref), [`Directed`](@ref), [`Fiducial`](@ref) and [`StateMask`](@ref).
