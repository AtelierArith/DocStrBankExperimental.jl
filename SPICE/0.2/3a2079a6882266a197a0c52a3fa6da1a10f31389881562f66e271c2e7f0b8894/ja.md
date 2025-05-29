```
gfdist(target, abcorr, obsrvr, relate, refval, adjust, step, nintvls, cnfine)
```

指定された観測者-ターゲット距離に関する制約が満たされる時間ウィンドウを返します。

### 引数

  * `target`: ターゲット天体の名前
  * `abcorr`: 収差補正フラグ
  * `obsrvr`: 観測天体の名前
  * `relate`: 関係演算子
  * `refval`: 参照値
  * `adjust`: 絶対極値探索のための調整値
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔数
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfdist_c.html)
