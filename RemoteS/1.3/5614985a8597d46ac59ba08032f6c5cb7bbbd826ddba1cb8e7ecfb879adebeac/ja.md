```
clip_orbits(track, BoundingBox::Vector{<:Real})
```

矩形の地理的領域内に含まれる軌道をクリップします。

  * `track`: 軌道の [lon, lat] 位置を持つ GMTdataset または Mx2 行列。これは通常、`sat_tracks` 関数を使用して計算されます。
  * `BoundingBox`: [lon*min, lon*max, lat*min, lat*max] で構成される領域の制限を持つベクトルです。

`BoundingBox` 領域内を横切る `tracks` のチャンクを持つ GMTdataset ベクトルを返します。

#例 `orb` が 2 日間にわたって sat_tracks() で計算された軌道を保持していると仮定し、20W-10E、30N-45N のウィンドウ内にクリップします。

```
D = clip_orbits(orb, [-20, 10, 30, 50]);
```
