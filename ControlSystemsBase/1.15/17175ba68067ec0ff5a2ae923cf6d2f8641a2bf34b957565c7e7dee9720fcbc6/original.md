```
mag = bodemag!(ws::BodemagWorkspace, sys::LTISystem, w::AbstractVector)
```

Compute the Bode magnitude operating in-place on an instance of [`BodemagWorkspace`](@ref). Note that the returned magnitude array is aliased with `ws.mag`. The output array `mag` is ∈ 𝐑(ny, nu, nω).
