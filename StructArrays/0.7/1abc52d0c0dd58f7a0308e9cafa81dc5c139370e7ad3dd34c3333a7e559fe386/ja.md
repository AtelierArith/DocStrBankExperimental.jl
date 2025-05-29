```
StructArray{T,N,C,I} <: AbstractArray{T, N}
```

型 `T` の構造体の `N` 次元配列を配列の構造として格納する型です。

  * `getindex` と `setindex!` は型 `T` の値を取得/設定するためにオーバーロードされています。
  * `getproperty` は個々のフィールド配列を返すためにオーバーロードされています。

# フィールド

  * `components`: 各フィールドで使用される配列の `NamedTuple` または `Tuple`。これらは [`components(x)`](@ref) でアクセスできます。
