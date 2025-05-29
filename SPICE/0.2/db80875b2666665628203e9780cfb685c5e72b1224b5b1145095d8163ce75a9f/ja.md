```
gftfov(inst, target, tshape, tframe, abcorr, obsrvr, step, nintvls, cnfine)
```

指定されたエフェメリスオブジェクトが指定された機器の視野（FOV）によって制約された空間と交差する時間間隔を決定します。

### 引数

  * `inst`: 機器の名前
  * `target`: 対象天体の名前
  * `tshape`: 対象天体に使用される形状モデルのタイプ
  * `tframe`: 対象天体の体固定、体中心フレーム
  * `abcorr`: 異常補正フラグ
  * `obsrvr`: 観測天体の名前
  * `step`: FOVイベントを見つけるためのステップサイズ（秒単位）
  * `nintvls`: ワークスペースウィンドウの間隔数
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gftfov_c.html)
