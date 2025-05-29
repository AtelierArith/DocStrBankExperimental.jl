```
struct QuantumObject{ObjType<:QuantumObjectType,DimType<:AbstractDimensions,DataType<:AbstractArray} <: AbstractQuantumObject{ObjType,DimType,DataType}
    data::DataType
    type::ObjType
    dimensions::DimType
end
```

時間に依存しない量子オブジェクトを表すJulia構造体。時間依存の場合については、[`QuantumObjectEvolution`](@ref)を参照してください。

!!! note "`dims` プロパティ"
    与えられた `H::QuantumObject` に対して、`H.dims` または `getproperty(H, :dims)` は、その `dimensions` を整数ベクトルの型で返します。


# 例

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
