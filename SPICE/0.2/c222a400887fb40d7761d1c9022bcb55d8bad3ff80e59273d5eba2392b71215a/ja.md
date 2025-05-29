```
gfrr(target, abcorr, obsrvr, relate, refval, adjust, step, nintvls, cnfine)
```

指定された制約が観測者-ターゲットの範囲速度に対して満たされる時間間隔を決定します。

### 引数

  * `target`: ターゲット天体の名前
  * `abcorr`: 異常修正フラグ
  * `obsrvr`: 観測天体の名前
  * `relate`: 関係演算子
  * `refval`: 参照値
  * `adjust`: 絶対極値検索のための調整値
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔数
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrr_c.html)
