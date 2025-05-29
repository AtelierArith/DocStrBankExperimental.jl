```
CellArray{T<:Cell,N,B,T_array} <: AbstractArray{T,N} where Cell <: Union{Number, SArray, FieldArray}
```

`N`次元配列で、要素の型は`T`であり、`T`はNumber、SArray、またはFieldArrayの型の`Cells`です。`B`はブロック長を定義し、同じ`Cell`フィールドの値が連続して格納される量を指します（`B=1`は構造体のようなストレージの配列を意味し、`B=prod(dims)`は配列のようなストレージの構造体の配列を意味します。`B=0`は`B=prod(dims)`のエイリアスであり、より専門的なディスパッチのおかげでパフォーマンスが向上します）。`T_array`はストレージに使用される配列の型を定義します。

---

```
CellArray{T,N,B}(T_arraykind, undef, dims)
CellArray{T,B}(T_arraykind, undef, dims)
CellArray{T}(T_arraykind, undef, dims)
```

型`T`の`Cells`を含む初期化されていない`N`次元`CellArray`を構築し、`T_arraykind`の型の配列に格納されます。

!!! note "パフォーマンスに関する注意"
    一般的に、GPUでの最良のパフォーマンスはデフォルトで設定されている`B=0`で得られます。特定のケースでは`B=1`がより良いパフォーマンスを発揮することがあります。現在の実装では、`B`の他の値はGPUでの最適なパフォーマンスにはつながりません。


参照: [`CPUCellArray`](@ref), [`CuCellArray`](@ref), [`ROCCellArray`](@ref)
