```
iswet(g, lat, lon, depth)
iswet(g, lats, lons, depths)
iswet(g, obs)
```

指定された位置が `g` の湿ったボックスに「入っている」かどうかを示す `BitArray` を返します。

技術的には、これは最近傍補間アルゴリズムを使用しているため、バウンディングボックスは完璧には機能しません。AIBECS がこの最近傍補間のみに依存する場合、Interpolations.jl を NearestNeighbors.jl に置き換えるのが良いかもしれません。
