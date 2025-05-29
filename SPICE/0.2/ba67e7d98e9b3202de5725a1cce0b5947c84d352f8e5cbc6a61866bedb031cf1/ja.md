```
gfevnt(udstep, udrefn, gquant, qnpars, lenvals, qpnams, qcpars, qdpars, qipars, qlpars,
       op, refval, tol, adjust, rpt, udrepi, udrepu, udrepf, nintvls, bail, udbail, cnfine)
```

指定された幾何量が指定された数学的条件を満たす時間間隔を決定します。

### 引数

  * `udstep`: 時間ステップを計算して返すルーチンの名前
  * `udrefn`: 精密な時間を計算するルーチンの名前
  * `gquant`: 幾何量のタイプ
  * `qpnams`: 量の定義パラメータの名前
  * `qcpars`: 文字の量定義パラメータの配列
  * `qdpars`: 倍精度の量定義パラメータの配列
  * `qipars`: 整数の量定義パラメータの配列
  * `qlpars`: 論理の量定義パラメータの配列
  * `op`: 極値（最大、最小、局所、絶対）を探すか、幾何量の値と数を比較する演算子
  * `refval`: 参照値
  * `tol`: 収束許容範囲（秒）
  * `adjust`: 絶対極値調整値
  * `rpt`: 進捗報告者のオン（`true`）またはオフ（`false`）
  * `udrepi`: 進捗報告を初期化する関数
  * `udrepu`: 進捗報告を更新する関数
  * `udrepf`: 進捗報告を最終化する関数
  * `nintvls`: ワークスペースウィンドウの間隔カウント
  * `cnfine`: 検索が制限されるSPICEウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfevnt_c.html)
