```
VonNeumann <: Stencil

VonNeumann(; radius=1, ndims=2)
VonNeumann(radius, ndims)
VonNeumann{R,N}()
```

Diamond-shaped neighborhood (in 2 dimensions), without the central cell In 1 dimension it is identical to [`Moore`](@ref).
