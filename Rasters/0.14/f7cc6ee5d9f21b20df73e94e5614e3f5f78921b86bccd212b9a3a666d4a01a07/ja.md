```
AbstractRasterStack
```

複数の [`AbstractRaster`](@ref) を保持するオブジェクトのための抽象スーパタイプで、空間次元を共有します。

これは `NamedTuple` に似た構造で、`AbstractRaster`(@ref) の `NamedTuple`、[`AbstractRaster`](@ref) をロードする文字列パス、または複数のレイヤーを含むファイルを指す単一のパス（NetCDF や HDF5 のような）を含むことができます。使用法と構文はすべてのケースで似ているか、同一です。

`AbstractRasterStack` は、いくつかまたはすべての次元を共有するレイヤーを保持できます。異なる長さや空間範囲を持つ同じ次元を持つレイヤーは存在できません。

`AbstractRasterStack` の `getindex` は一般的にメモリバックされた標準の [`Raster`](@ref) を返します。`raster[:somelayer] |> plot` はレイヤー配列をプロットし、`raster[:somelayer, X(1:100), Band(2)] |> plot` は全体の配列をロードせずにサブセットをプロットします。

`getindex` をキーで使用した `AbstractRasterStack` は、スタック内のすべての配列に `getindex` を適用した別のスタックを返します。
