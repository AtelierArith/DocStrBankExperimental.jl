```
VIDAMovie(mov::IntensityMap{T,3})
```

フレーム間の簡単な補間のためのVIDAMovieクラスを作成します。

# 引数

  * `mov`: 映画のフレームを表す軸(:X, :Y, :T)を持つIntensityMap。時間次元は等間隔である必要はありません。

# 戻り値

`IntensityMap`のように振る舞う`VIDAMovie`オブジェクトですが、フレーム間の補間を[`get_image(vida_movie, time)`](@ref)を使って行うことができます。
