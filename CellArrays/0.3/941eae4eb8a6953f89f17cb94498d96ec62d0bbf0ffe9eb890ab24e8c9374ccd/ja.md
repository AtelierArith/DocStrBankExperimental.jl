```
@define_ROCCellArray
```

呼び出しモジュールで次の型エイリアスとコンストラクタを定義します：

---

```
ROCCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`次元のCellArrayで、タイプ`T`のセル、ブロック長`B`、および`T_array`が要素タイプ`T_elem`の`ROCArray`である：`CellArray{T,N,B,ROCArray{T_elem,CellArrays._N}}`のエイリアス。

---

```
ROCCellArray{T,B}(undef, dims)
ROCCellArray{T}(undef, dims)
```

タイプ`T`の`Cells`を含む初期化されていない`N`次元の`CellArray`を構築し、これらは`ROCArray`の配列に格納されます。

参照： [`CellArray`](@ref), [`CPUCellArray`](@ref), [`CuCellArray`](@ref) ********************************************************************************

!!! note "不要な依存関係を避ける"
    GPU `CellArray`のための型エイリアスとコンストラクタは、CellArraysのGPUパッケージへの不要な依存関係を避けるためにマクロを介して提供されます。


参照： [`@define_CuCellArray`](@ref)
