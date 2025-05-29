```
compute_saddle(bsn_nfo::BasinInfo, integ; max_iter=10)
```

このアルゴリズムは、動的システムの引力盆の境界にある鞍点を求めます。境界がフラクタルである場合、この集合はカオティックサドルとして知られ、システムの過渡的な動力学に関与します。鞍点はSaddle-Straddleアルゴリズムを用いて計算されます。2つの`一般化盆`を定義する必要があり、すなわち盆を2つの集合に分けなければなりません（キーワード引数も参照）。

[H. E. Nusse and J. A. Yorke, Dynamics: numerical explorations, Springer, New York, 2012]

## 引数

  * `bsn_nfo` : 盆の情報とマップ関数を保持する構造体。この構造体は、盆が最初に`basin_stroboscopic_map`または`basin_poincare_map`で計算されるときに設定されます。
  * `integ` : 盆の情報を含む行列。
  * `bas_A` : 一般化盆Aを表すアトラクタのインデックスを持つベクトル
  * `bas_B` : 一般化盆Bを表すアトラクタのインデックスを持つベクトル。`bas_A ∪ bas_B = [1:N]` かつ `bas_A ∩ bas_B = ∅` であることに注意してください。

## キーワード引数

  * `N` : 計算する鞍点の数
  * `init_tol`: ストラドルセグメントの長さ

## 例

```
# 一般化A = [1] と盆B = [2,3] の間に1000点を計算する
sa,sb = compute_saddle(bsn, integ_df, [1], [2,3],1000)
# saは「左」集合で、sbは右「集合」です
```
