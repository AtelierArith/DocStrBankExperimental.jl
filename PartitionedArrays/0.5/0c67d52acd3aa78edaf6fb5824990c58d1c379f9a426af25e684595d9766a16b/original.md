```
struct PRange{A}
```

`PRange` (partitioned range) is a type representing a range of indices `1:n` partitioned into several parts. This type is used to represent the axes of instances of [`PVector`](@ref) and [`PSparseMatrix`](@ref).

# Properties

  * `partition::A`

The item `partition[i]` is an object that contains information about the own, ghost, and local indices of part number `i`. `typeof(partition[i])` is a type that implements the methods of the [`AbstractLocalIndices`](@ref) interface. Use this interface to access the underlying information about own, ghost, and local indices.

# Supertype hierarchy

```
PRange{A} <: AbstractUnitRange{Int}
```
