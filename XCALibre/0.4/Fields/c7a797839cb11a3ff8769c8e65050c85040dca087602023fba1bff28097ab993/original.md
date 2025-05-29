```
struct VectorField{S1<:ScalarField,S2,S3,M<:AbstractMesh,BC} <: AbstractVectorField
    x::S1   # x-component is itself a `ScalarField`
    y::S2   # y-component is itself a `ScalarField`
    z::S3   # z-component is itself a `ScalarField`
    mesh::M
    BCs::BC
end
```
