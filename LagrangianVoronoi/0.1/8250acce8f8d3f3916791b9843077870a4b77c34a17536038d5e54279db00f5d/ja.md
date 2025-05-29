```
populate_lloyd!(grid::VoronoiGrid{T}; charfun, niterations, ic!)
```

計算領域を同心円状に配置された多角形で埋めます。キーワードパラメータ：

  * `charfun`: 特徴関数; `charfun(x) = true` である領域のみが埋められます
  * `center`: 各円の中心
  * `ic!`: 初期条件; メッシュが生成された後にすべての多角形に対して `ic!(p)` が呼び出されます
