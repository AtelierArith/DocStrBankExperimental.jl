```
gfuds!(udfuns, udqdec, relate, refval, adjust, step, nintvls, cnfine, result)
```

ユーザー定義スカラー量に対してGF検索を実行します。

### 引数

  * `udfuns`: ある時刻における関心のあるスカラー量を計算するルーチンの名前、例: `f(et) = ...`
  * `udqdec`: スカラー量が減少しているかどうかを計算するルーチンの名前、例: `g(f, et) = ...`
  * `relate`: 極値（最大、最小、局所、絶対）を探すか、幾何学的量の値と数を比較する演算子
  * `refval`: スカラー量の条件の基準として使用される値
  * `adjust`: 絶対的な極値幾何学的条件に対する許容変動
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔カウント
  * `cnfine`: 検索が制限されるSPICEウィンドウ
  * `result`: 結果を含むSPICEウィンドウ

### 出力

`result`を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfuds_c.html)
