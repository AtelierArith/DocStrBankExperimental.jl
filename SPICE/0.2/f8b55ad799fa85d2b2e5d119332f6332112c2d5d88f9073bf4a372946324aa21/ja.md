```
gffove!(inst, tshape, raydir, target, tframe, abcorr, obsrvr, tol,
        udstep, udrefn, rpt, udrepi, udrepu, udrepf, cnfine, result)
```

指定されたターゲット天体または光線が指定された機器の視野（FOV）によって制限された空間と交差する時間間隔を決定します。

### 引数

  * `inst`: 機器の名前
  * `tshape`: ターゲット天体に使用される形状モデルのタイプ
  * `raydir`: 光線の方向ベクトル
  * `target`: ターゲット天体の名前
  * `tframe`: ターゲット天体の体固定、体中心フレーム
  * `abcorr`: 異常補正フラグ
  * `obsrvr`: 観測天体の名前
  * `tol`: 秒単位の収束許容範囲
  * `udstep`: 時間ステップを返すルーチンの名前
  * `udrefn`: 精密な時間を計算するルーチンの名前
  * `rpt`: 進捗報告フラグ
  * `udrepi`: 進捗報告を初期化する関数
  * `udrepu`: 進捗報告を更新する関数
  * `udrepf`: 進捗報告を最終化する関数
  * `cnfine`: 検索が制限されるSPICEウィンドウ
  * `result`: 結果を含むウィンドウ

### 出力

`result`を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gffove_c.html)
