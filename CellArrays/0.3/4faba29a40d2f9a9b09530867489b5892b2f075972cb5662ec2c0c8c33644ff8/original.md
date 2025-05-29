```
CPUCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`-dimensional CellArray with cells of type `T`, blocklength `B`, and `T_array` being an `Array` of element type `T_elem`: alias for `CellArray{T,N,B,Array{T_elem,CellArrays._N}}`.

---

```
CPUCellArray{T,B}(undef, dims)
CPUCellArray{T}(undef, dims)
```

Construct an uninitialized `N`-dimensional `CellArray` containing `Cells` of type `T` which are stored in an array of kind `Array`.

See also: [`CellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref)
