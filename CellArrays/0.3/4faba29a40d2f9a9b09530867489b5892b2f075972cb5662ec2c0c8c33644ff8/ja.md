```
CPUCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`次元のCellArrayで、型`T`のセル、ブロック長`B`、および`T_array`が要素型`T_elem`の`Array`である: `CellArray{T,N,B,Array{T_elem,CellArrays._N}}`のエイリアス。

---

```
CPUCellArray{T,B}(undef, dims)
CPUCellArray{T}(undef, dims)
```

型`T`の`Cells`を含む初期化されていない`N`次元の`CellArray`を構築し、これは`Array`の配列に格納されます。

参照: [`CellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref)
