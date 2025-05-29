```
profile(h::Hist2D, axis::Symbol=:x)
profile(axis::Symbol=:x) = h::Hist2D -> profile(h, axis)
```

2D ヒストグラムの `axis` プロファイルを、他の軸に対する重み付き平均を計算することで返します。 `profile(h, :x)` は、`h` の y 軸エッジを持つ `Hist1D` を返します。
