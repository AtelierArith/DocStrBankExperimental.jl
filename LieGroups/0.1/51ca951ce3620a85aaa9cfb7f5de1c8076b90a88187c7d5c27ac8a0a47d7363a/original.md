```
ProductGroupOperation{O<:NTuple{N,AbstractGroupOperation} where N} <: AbstractProductGroupOperation
```

A struct do model a tuple of group operations, one for each factor of a product group, that together forms a new group operation.

Access to the single operations can be done by `pgo[i]`.

# Constructor

```
ProductGroupOperation(o::AbstractGroupOperation...)
×(o::AbstractGroupOperation...) = ProductGroupOperation(o...)
```
