```
ManyPencilArray{T,N,M} <: AbstractManyPencilArray{N,M}
```

`M` 番目の異なる [`PencilArray`](@ref) ビューを同じ基盤データバッファに保持するコンテナです。すべてのビューは同じ要素型 `T` と次元数 `N` を共有します。

これは、[`transpose!`](@ref Transpositions.transpose!) を使用してインプレースデータ転置を実行するために使用できます。

---

```
ManyPencilArray{T}(undef, pencils...; extra_dims=())
```

与えられたすべての [`Pencil`](@ref) に関連付けられた型 `T` のデータを保持できる `ManyPencilArray` コンテナを作成します。

オプションの `extra_dims` 引数は、[`PencilArray`](@ref) と同じです。
