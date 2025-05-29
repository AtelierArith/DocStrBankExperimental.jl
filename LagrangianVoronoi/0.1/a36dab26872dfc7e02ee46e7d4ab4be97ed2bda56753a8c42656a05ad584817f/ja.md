```
populate_rect!(grid::VoronoiGrid{T}; charfun, ic!)
```

計算領域を直交格子で埋めます。キーワードパラメータ：

  * `charfun`: 特徴関数; `charfun(x) = true` である領域のみが埋められます
  * `ic!`: 初期条件; メッシュが生成された*後*に、すべての多角形に対して `ic!(p)` が呼び出されます
