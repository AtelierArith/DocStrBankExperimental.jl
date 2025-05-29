```
@index
```

The `@index` macro can be used to give you the index of a workitem within a kernel function. It supports both the production of a linear index or a cartesian index. A cartesian index is a general N-dimensional index that is derived from the iteration space.

# Index granularity

  * `Global`: Used to access global memory.
  * `Group`: The index of the `workgroup`.
  * `Local`: The within `workgroup` index.

# Index kind

  * `Linear`: Produces an `Int64` that can be used to linearly index into memory.
  * `Cartesian`: Produces a `CartesianIndex{N}` that can be used to index into memory.
  * `NTuple`: Produces a `NTuple{N}` that can be used to index into memory.

If the index kind is not provided it defaults to `Linear`, this is subject to change.

# Examples

```julia
@index(Global, Linear)
@index(Global, Cartesian)
@index(Local, Cartesian)
@index(Group, Linear)
@index(Local, NTuple)
@index(Global)
```
