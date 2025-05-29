```
CellArray{T<:Cell,N,B,T_array} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`-dimensional array with elements of type `T`, where `T` are `Cells` of type Number, SArray or FieldArray. `B` defines the blocklength, which refers to the amount of values of a same `Cell` field that are stored contigously (`B=1` means array of struct like storage; `B=prod(dims)` means array struct of array like storage; `B=0` is an alias for `B=prod(dims)`, enabling better peformance thanks to more specialized dispatch). `T_array` defines the array type used for storage.

---

```
CellArray{T,N,B}(T_arraykind, undef, dims)
CellArray{T,B}(T_arraykind, undef, dims)
CellArray{T}(T_arraykind, undef, dims)
```

Construct an uninitialized `N`-dimensional `CellArray` containing `Cells` of type `T` which are stored in an array of kind `T_arraykind`.

!!! note "Performance note"
    Best performance on GPUs is in general obtained with `B=0` as set by default. `B=1` migth give better performance in certain cases. Other values of `B` do with the current implementation not lead to optimal performance on GPU.


See also: [`CPUCellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref)
