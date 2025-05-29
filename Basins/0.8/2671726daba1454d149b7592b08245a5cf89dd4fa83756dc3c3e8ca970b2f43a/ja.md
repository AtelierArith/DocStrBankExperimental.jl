```
detect_wada_grid_method(integ, bsn_nfo::BasinInfo; max_iter=10)
```

このアルゴリズムは、動的システムにおけるワダ盆地のテストを行います。すべてのアトラクタが境界に表現されているかどうかを確認するために、動的システムを使用します。

[A. Daza, A. Wagemakers, M. A. F. Sanjuán and J. A. Yorke, Testing for Basins of Wada, Sci. Rep., 5, 16579 (2015)]

## 引数

  * `integ` : 盆地の情報を含む行列。
  * `bsn_nfo` : 盆地の情報とマップ関数を保持する構造体。この構造体は、`basin_stroboscopic_map` または `basin_poincare_map` で盆地が最初に計算されるときに設定されます。

## キーワード引数

  * `max_iter` : アトラクタを探すための分割の最大深さを設定します。各ステップでポイントの数が倍増します。
