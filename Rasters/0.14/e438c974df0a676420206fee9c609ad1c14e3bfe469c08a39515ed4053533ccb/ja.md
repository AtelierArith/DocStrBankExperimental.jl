```
reproject(obj; crs)
```

`obj`のルックアップを異なるcrsに再投影します。

これはラスターデータにとってロスレスな操作であり、ルックアップ値のみが変更されます。これは、ソースと宛先の投影の軸が整列している場合にのみ可能です：変更は通常、[`Regular`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Lookups.Regular)と[`Irregular`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Lookups.Irregular)ルックアップスパンの間で行われます。

回転、傾斜、または何らかの方法で歪んだ投影間の変換には、[`resample`](@ref)を使用してください。

`AbstractProjected`ルックアップ（例えば`Ti`次元）のない次元は、変更されることなく静かに返されます。

# 引数

  * `obj`: `Lookup`、`Dimension`、`Dimension`の`Tuple`、`Raster`または`RasterStack`。
  * `crs`: `to`が渡されない場合に結果のラスタに添付される`crs`、または`Extent`です。それ以外の場合は、`to`からのcrsが使用されます。
