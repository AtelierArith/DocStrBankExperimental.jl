```
tensor(x::Basis, y::Basis, z::Basis...)
```

Create a [`CompositeBasis`](@ref) from the given bases.

Any given CompositeBasis is expanded so that the resulting CompositeBasis never contains another CompositeBasis.
