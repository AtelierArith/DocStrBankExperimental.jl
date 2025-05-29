```
struct VectorField{S1<:ScalarField,S2,S3,M<:AbstractMesh,BC} <: AbstractVectorField
    x::S1   # x成分はそれ自体が`ScalarField`
    y::S2   # y成分はそれ自体が`ScalarField`
    z::S3   # z成分はそれ自体が`ScalarField`
    mesh::M
    BCs::BC
end
```
