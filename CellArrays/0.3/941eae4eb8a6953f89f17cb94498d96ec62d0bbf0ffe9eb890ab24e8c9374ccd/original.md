```
@define_ROCCellArray
```

Define the following type alias and constructors in the caller module:

---

```
ROCCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`-dimensional CellArray with cells of type `T`, blocklength `B`, and `T_array` being a `ROCArray` of element type `T_elem`: alias for `CellArray{T,N,B,ROCArray{T_elem,CellArrays._N}}`.

---

```
ROCCellArray{T,B}(undef, dims)
ROCCellArray{T}(undef, dims)
```

Construct an uninitialized `N`-dimensional `CellArray` containing `Cells` of type `T` which are stored in an array of kind `ROCArray`.

See also: [`CellArray`](@ref), [`CPUCellArray`](@ref), [`CuCellArray`](@ref) ********************************************************************************

!!! note "Avoiding unneeded dependencies"
    The type aliases and constructors for GPU `CellArray`s are provided via macros to avoid unneeded dependencies on the GPU packages in CellArrays.


See also: [`@define_CuCellArray`](@ref)
