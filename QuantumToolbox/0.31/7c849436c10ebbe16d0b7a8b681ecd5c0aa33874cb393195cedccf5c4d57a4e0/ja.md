```
抽象型 AbstractQuantumObject{ObjType,DimType,DataType}
```

[`QuantumObject`](@ref) や [`QuantumObjectEvolution`](@ref) のようなすべての量子オブジェクトのための抽象型。

# 例

```jldoctest
julia> sigmax() isa AbstractQuantumObject
true
```
