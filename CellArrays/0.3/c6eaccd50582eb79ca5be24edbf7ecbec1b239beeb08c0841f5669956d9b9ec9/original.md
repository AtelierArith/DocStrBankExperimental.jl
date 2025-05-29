```
@define_CuCellArray
```

Define the following type alias and constructors in the caller module:

---

```
CuCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`-dimensional CellArray with cells of type `T`, blocklength `B`, and `T_array` being a `CuArray` of element type `T_elem`: alias for `CellArray{T,N,B,CuArray{T_elem,CellArrays._N,CUDA.DeviceMemory}}`.

---

```
CuCellArray{T,B}(undef, dims)
CuCellArray{T}(undef, dims)
```

Construct an uninitialized `N`-dimensional `CellArray` containing `Cells` of type `T` which are stored in an array of kind `CuArray`.

See also: [`CellArray`](@ref), [`CPUCellArray`](@ref), [`ROCCellArray`](@ref) ********************************************************************************

!!! note "Avoiding unneeded dependencies"
    The type aliases and constructors for GPU `CellArray`s are provided via macros to avoid unneeded dependencies on the GPU packages in CellArrays.


See also: [`@define_ROCCellArray`](@ref)
