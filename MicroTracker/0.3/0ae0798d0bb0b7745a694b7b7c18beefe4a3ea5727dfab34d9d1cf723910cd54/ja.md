```
find_trajectory_bounds(df_1particle::AbstractDataFrame, video_resolution::Tuple{Int, Int})
```

フレーム番号のタプル `(low, high)` を返します。ここで、すべての軌道ポイントが範囲内にあります。

これは粒子の半径を計算し、軌道の中心から前方と後方に繰り返し移動して、範囲外のポイントを見つけるまで続けます。これが軌道の高い境界と低い境界です。
