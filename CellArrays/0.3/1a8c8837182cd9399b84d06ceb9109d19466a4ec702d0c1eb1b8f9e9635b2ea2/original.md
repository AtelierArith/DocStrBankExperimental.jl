```
@define_MtlCellArray
```

Define the following type alias and constructors in the caller module:

---

```
MtlCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`-dimensional CellArray with cells of type `T`, blocklength `B`, and `T_array` being a `MtlArray` of element type `T_elem`: alias for `CellArray{T,N,B,MtlArray{T_elem,CellArrays._N}}`.

---

```
MtlCellArray{T,B}(undef, dims)
MtlCellArray{T}(undef, dims)
```

Construct an uninitialized `N`-dimensional `CellArray` containing `Cells` of type `T` which are stored in an array of kind `MtlArray`.

See also: [`CellArray`](@ref), [`CPUCellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref) ********************************************************************************

!!! note "Avoiding unneeded dependencies"
    The type aliases and constructors for GPU `CellArray`s are provided via macros to avoid unneeded dependencies on the GPU packages in CellArrays.


See also: [`@define_CuCellArray`](@ref), [`@define_ROCCellArray`](@ref)
