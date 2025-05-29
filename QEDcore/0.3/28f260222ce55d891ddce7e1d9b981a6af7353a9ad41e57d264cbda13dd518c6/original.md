```julia
struct SLorentzVector{T} <: QEDbase.AbstractLorentzVector{T}
```

Concrete implementation of a generic static Lorentz vector. Each manipulation of an concrete implementation which is not self-contained (i.e. produces the same Lorentz vector type) will result in this type.

# Fields

  * `t::Any`: `t` component
  * `x::Any`: `x` component
  * `y::Any`: `y` component
  * `z::Any`: `z` component
