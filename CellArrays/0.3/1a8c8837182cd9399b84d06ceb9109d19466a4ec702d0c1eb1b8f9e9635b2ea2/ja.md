```
@define_MtlCellArray
```

次の型エイリアスとコンストラクタを呼び出しモジュールで定義します：

---

```
MtlCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`次元のCellArrayで、タイプ`T`のセル、ブロック長`B`、および`T_array`が要素タイプ`T_elem`の`MtlArray`である：`CellArray{T,N,B,MtlArray{T_elem,CellArrays._N}}`のエイリアス。

---

```
MtlCellArray{T,B}(undef, dims)
MtlCellArray{T}(undef, dims)
```

タイプ`T`の`Cells`を含む初期化されていない`N`次元の`CellArray`を構築し、これらは`MtlArray`の配列に格納されます。

参照： [`CellArray`](@ref), [`CPUCellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref) ********************************************************************************

!!! note "不必要な依存関係を避ける"
    GPU `CellArray`のための型エイリアスとコンストラクタは、CellArraysのGPUパッケージへの不必要な依存関係を避けるためにマクロを介して提供されます。


参照： [`@define_CuCellArray`](@ref), [`@define_ROCCellArray`](@ref)
