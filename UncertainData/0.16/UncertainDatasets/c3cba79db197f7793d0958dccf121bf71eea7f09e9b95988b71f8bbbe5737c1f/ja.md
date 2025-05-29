```
UVAL_COLLECTION_TYPES = Union{UD, UV} where {
    UD <: AbstractUncertainValueDataset, 
    UV <: AbstractVector{T} where {
        T <: AbstractUncertainValue}}
```

不確実な値のタイプを表すために使用される型の和集合。
