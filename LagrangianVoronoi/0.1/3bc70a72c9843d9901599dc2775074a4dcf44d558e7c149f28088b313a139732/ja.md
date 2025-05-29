```
populate_circ!(grid::VoronoiGrid{T}; charfun, center, ic!)
```

同心円に配置された多角形で計算領域を埋めます。キーワードパラメータ：

  * `charfun`: 特徴関数; `charfun(x) = true` である領域のみが埋められます
  * `center`: 各円の中心
  * `ic!`: 初期条件; メッシュが生成された後にすべての多角形に対して `ic!(p)` が呼び出されます
