```
convex_hull(X::LazySet, Y::LazySet; [algorithm]=nothing,
            [backend]=nothing, [solver]=nothing)
```

2つの多面体集合の凸包を計算します。

### 入力

  * `X`         – 多面体集合
  * `Y`         – 多面体集合
  * `algorithm` – （オプション、デフォルト: `nothing`）凸包アルゴリズム
  * `backend`   – （オプション、デフォルト: `nothing`）多面体計算のためのバックエンド（高次元集合に使用）
  * `solver`    – （オプション、デフォルト: `nothing`）バックエンドで使用される線形計画ソルバー

### 出力

集合が空である場合、結果は `EmptySet` です。凸包が単一の点で構成される場合、結果は `Singleton` です。入力集合が1次元の場合、結果は `Interval` です。入力集合が2次元の場合、結果は `VPolygon` です。それ以外の場合、結果は `VPolytope` です。

### アルゴリズム

`vertices_list` を使用して `X` と `Y` の頂点を計算し、それらの頂点の和集合の凸包を計算します。
