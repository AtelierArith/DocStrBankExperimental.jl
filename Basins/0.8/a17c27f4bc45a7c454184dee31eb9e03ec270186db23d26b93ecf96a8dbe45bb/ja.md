```
detect_wada_merge_method(xg,yg, basin)
```

アルゴリズムは、マージされた流域間の最大および最小ハウスドルフ距離を提供します。これらの2つの距離は、流域がワダ特性を持つかどうかを判断するのに役立ちます。

[A. Daza, A. Wagemakers and M. A. F. Sanjuán, Ascertaining when a basin is Wada: the merging method, Sci. Rep., 8, 9954 (2018)]

## 引数

  * `basin` : 流域の情報を含む行列。
  * `xg`, `yg` : テストする初期条件のグリッドを定義する1次元範囲ベクトル。

## 例

```
max_dist,min_dist = detect_wada_merge_method(basin,xg,yg)
# グリッド解像度
epsilon = xg[2]-xg[1]
# dmaxが大きい場合、これはワダではない
@show dmax = max_dist/epsilon
@show dmin = min_dist/epsilon
```
