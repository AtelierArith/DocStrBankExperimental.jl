```julia
get_image(mov, t; keeptime)

```

ムービーオブジェクト `mov` の時間 t でのフレームを取得します。これは、要求された時間で `IntensityMap` オブジェクトを返します。返されるオブジェクトは線形補間によって見つかります。
