```
gfpa(result, target, illmn, abcorr, obsrvr, relate, refval, adjust, step, nintvls, cnfine)
```

指定された制約が満たされる時間間隔を決定します。これは、照明源、ターゲット、および観測者の天体中心間の位相角に関するものです。

### 引数

  * `target`: ターゲット天体の名前
  * `illmn`: 照明天体の名前
  * `abcorr`: 異常補正フラグ
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

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfpa_c.html)
