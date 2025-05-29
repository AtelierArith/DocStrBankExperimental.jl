```
@define_CuCellArray
```

次の型エイリアスとコンストラクタを呼び出しモジュールで定義します：

---

```
CuCellArray{T<:Cell,N,B,T_elem} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`次元のCellArrayで、型`T`のセル、ブロック長`B`、および`T_array`が要素型`T_elem`の`CuArray`である：`CellArray{T,N,B,CuArray{T_elem,CellArrays._N,CUDA.DeviceMemory}}`のエイリアス。

---

```
CuCellArray{T,B}(undef, dims)
CuCellArray{T}(undef, dims)
```

型`T`の`Cells`を含む初期化されていない`N`次元の`CellArray`を構築し、これは`CuArray`の配列に格納されます。

参照： [`CellArray`](@ref), [`CPUCellArray`](@ref), [`ROCCellArray`](@ref) ********************************************************************************

!!! note "不要な依存関係を避ける"
    GPU `CellArray`のための型エイリアスとコンストラクタは、CellArraysのGPUパッケージへの不要な依存関係を避けるためにマクロを介して提供されます。


参照： [`@define_ROCCellArray`](@ref)
