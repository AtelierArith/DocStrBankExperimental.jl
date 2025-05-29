```
SparseTensor{Tv,Ti,N} <: AbstractSparseArray{Tv, Ti, N}
```

A sparse tensor is a multi-dimensional array that is stored in a sparse format.

# Fields

  * `size::NTuple{N, Int}`: the size of the tensor
  * `strides::NTuple{N, Ti}`: the strides of the tensor
  * `data::Dict{Ti, Tv}`: the data of the tensor
