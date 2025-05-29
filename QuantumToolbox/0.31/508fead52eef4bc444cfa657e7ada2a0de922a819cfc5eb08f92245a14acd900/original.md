```
struct QuantumObject{ObjType<:QuantumObjectType,DimType<:AbstractDimensions,DataType<:AbstractArray} <: AbstractQuantumObject{ObjType,DimType,DataType}
    data::DataType
    type::ObjType
    dimensions::DimType
end
```

Julia structure representing any time-independent quantum objects. For time-dependent cases, see [`QuantumObjectEvolution`](@ref).

!!! note "`dims` property"
    For a given `H::QuantumObject`, `H.dims` or `getproperty(H, :dims)` returns its `dimensions` in the type of integer-vector.


# Examples

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> a isa QuantumObject
true

julia> a.dims
1-element StaticArraysCore.SVector{1, Int64} with indices SOneTo(1):
 20

julia> a.dimensions
Dimensions{1, Tuple{Space}}((Space(20),))
```
