```
spread2(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Matrix{<:Real}; res=1, limit=Inf, iterations=3)
```

摩擦コストのためのプッシュブルーム法は、*Eastman (1989) [^eastman1989] によって議論されています。この方法は、[ ^tomlin1983] 方法よりもはるかにスケールが良い（線形）はずですが、迷路のような交差できない障害物がある場合、デフォルト（3）で設定されたよりも多くの `iterations` を必要とすることがあります。

# 出力

  * `Array{Float64,2}` 合計摩擦距離

# 引数

  * `points::Matrix{<:Real}` 入力配列
  * `initial::Matrix{<:Real}` 標高を誇張するための係数
  * `friction::Matrix{<:Real}` セルサイズの解像度
  * `res=1` 解像度またはセルサイズ
  * `limit=Inf` 初期フィル値
  * `iterations=3` プッシュブルームの反復回数

[^eastman1989]: Eastman, J. Ronald. 1989. ‘Pushbroom Algorithms for Calculating Distances in Raster Grids’. In Proceedings, Autocarto, 9:288–97.

```
