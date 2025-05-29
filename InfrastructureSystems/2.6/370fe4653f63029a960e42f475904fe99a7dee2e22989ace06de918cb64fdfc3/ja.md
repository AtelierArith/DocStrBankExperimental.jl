```
CompressionSettings(enabled, type, level, shuffle)
```

HDF5圧縮設定のカスタマイズを提供します。

  * `enabled::Bool`: 圧縮が有効かどうかを制御します。
  * `type::InfrastructureSystems.CompressionTypesModule.CompressionTypes`: 使用する圧縮の種類を指定します。
  * `level::Int64`: サポートされている値は0-9です。高い値はより良い圧縮率を提供しますが、時間がかかります。
  * `shuffle::Bool`: シャッフルフィルターを有効にするかどうかを制御します。DEFLATEと共に使用されます。

オプションの詳細については、[HDF5.jl](https://juliaio.github.io/HDF5.jl/stable/)および[HDF5](https://portal.hdfgroup.org/)のドキュメントを参照してください。

# 例

```julia
settings = CompressionSettings(
    enabled = true,
    type = CompressionTypes.DEFLATE,  # BLOSCもサポートされています
    level = 3,
    shuffle = true,
)
```
