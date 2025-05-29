```
gfrfov(inst, raydir, rframe, abcorr, obsrvr, step, cnfine, maxwin=10000)
```

指定された機器の視野（FOV）によって制約された空間と交差する指定された光線の時間間隔を決定します。

### 引数

  * `inst`: 機器の名前
  * `raydir`: 光線の方向ベクトル
  * `rframe`: 光線の方向ベクトルの基準フレーム
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測対象の名前
  * `step`: FOVイベントを見つけるための秒単位のステップサイズ
  * `cnfine`: 検索が制限されるSPICEウィンドウ
  * `maxwin`: 出力ウィンドウの最大長（デフォルト: 10000）

### 出力

結果を含むウィンドウを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrfov_c.html)
