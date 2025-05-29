```
struct Momentum{V,S,SS} <: AbstractMomentumModel
    U::V 
    p::S 
    sources::SS
end
```

Momentum model containing key momentum fields.

### Fields

  * 'U'        – Velocity VectorField.
  * 'p'        – Pressure ScalarField.
  * 'sources'  – Momentum model sources.

### Examples

  * `Momentum(mesh::AbstractMesh)
