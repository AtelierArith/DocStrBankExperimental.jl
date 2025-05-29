```
spread(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Matrix{<:Real}; res=1, limit=Inf)
```

`points`からの総摩擦距離の拡散は、*Tomlin (1983)* によるものです [^tomlin1983]。これは、[PCRaster](https://pcraster.geo.uu.nl/pcraster/4.0.2/doc/manual/op_spread.html) によって実装された方法でもあります。

# 出力

  * `Array{Float64,2}` 総摩擦距離

# 引数

  * `points::Matrix{<:Real}` 入力配列
  * `initial::Matrix{<:Real}` 標高を誇張するための係数
  * `friction::Matrix{<:Real}` セルサイズの解像度
  * `res=1` 解像度またはセルサイズ
  * `limit=Inf` 初期充填値

[^tomlin1983]: Tomlin, Charles Dana. 1983. Digital Cartographic Modeling Techniques in Environmental Planning. Yale University.
