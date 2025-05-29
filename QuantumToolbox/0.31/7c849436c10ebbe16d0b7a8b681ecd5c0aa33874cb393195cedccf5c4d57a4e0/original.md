```
abstract type AbstractQuantumObject{ObjType,DimType,DataType}
```

Abstract type for all quantum objects like [`QuantumObject`](@ref) and [`QuantumObjectEvolution`](@ref).

# Example

```jldoctest
julia> sigmax() isa AbstractQuantumObject
true
```
