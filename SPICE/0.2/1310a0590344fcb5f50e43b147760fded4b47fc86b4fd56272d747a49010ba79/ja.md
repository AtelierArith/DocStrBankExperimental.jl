```
gfilum(method, angtyp, target, illmn, fixref, abcorr, obsrvr, spoint, relate, refval,
       adjust, step, nintvls, cnfine)
```

指定されたターゲットボディの表面点における観測された位相、太陽入射角、または放射角に関する制約が満たされる時間ウィンドウを返します。

### 引数

  * `method`: 計算方法
  * `angtyp`: 照明角のタイプ
  * `target`: ターゲットボディの名前
  * `illmn`: 照明源の名前
  * `fixref`: ボディ固定、ボディ中心のターゲットボディフレーム
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測ボディの名前
  * `spoint`: ターゲット表面点のボディ固定座標
  * `relate`: 関係演算子
  * `refval`: 参照値
  * `adjust`: 絶対極値検索のための調整値
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔カウント
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfilum_c.html)
