```
populate_vogel!(grid::VoronoiGrid{T}; charfun, center, ic!)
```

ポリゴンをボーゲルスパイラルに配置して計算領域を埋めます。キーワードパラメータ：

  * `charfun`: 特徴関数; `charfun(x) = true` の場合のみ、その領域が埋められます
  * `center`: スパイラルの中心
  * `ic!`: 初期条件; メッシュが生成された後に、すべてのポリゴンに対して `ic!(p)` が呼び出されます
