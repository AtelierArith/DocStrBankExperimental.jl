```
struct ExtensionFrame{S,T} <: DerivedDict{S,T}
```

An ExtensionFrame is the restriction of a basis to a subset of its domain. This results in a frame that implicitly represents extensions of functions on the smaller set to the larger set.

Created by the function `extensionframe`.

See also [`extensionframe`](@ref)

```jldocs
julia> extensionframe(Fourier(10),0.0..0.5)
```
