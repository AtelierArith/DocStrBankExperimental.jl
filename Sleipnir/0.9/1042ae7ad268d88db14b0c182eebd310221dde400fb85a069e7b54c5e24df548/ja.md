```
apply_t_grad!(climate::RasterStack, dem::Raster)
```

デジタル標高モデル（DEM）に基づいて気候データに温度勾配を適用します。

# 引数

  * `climate::RasterStack`: 温度および勾配情報を含む気候データを含む `RasterStack` オブジェクト。
  * `dem::Raster`: デジタル標高モデル（DEM）データを表す `Raster` オブジェクト。

# 説明

この関数は、温度勾配を適用することによって `climate` オブジェクト内の温度データを調整します。調整は、DEMデータからの平均標高と `climate` オブジェクトのメタデータに指定された基準高さとの違いに基づいています。
