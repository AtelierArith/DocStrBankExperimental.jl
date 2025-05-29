```
UVAL_COLLECTION_TYPES = Union{UD, UV} where {
    UD <: AbstractUncertainValueDataset, 
    UV <: AbstractVector{T} where {
        T <: AbstractUncertainValue}}
```

A type union used to represent types of uncertain values. 
