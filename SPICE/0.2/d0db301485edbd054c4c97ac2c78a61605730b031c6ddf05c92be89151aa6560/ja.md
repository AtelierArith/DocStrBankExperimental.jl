```
gfsntc(target, fixref, method, abcorr, obsrvr, dref, dvec, crdsys, coord, relate, refval,
       adjust, step, nintvls, cnfine)
```

座標が数値制約を満たす表面交差位置ベクトルの時間間隔を決定します。

### 引数

  * `target`: 対象天体の名前
  * `fixref`: `target` に関連付けられた天体固定フレーム
  * `method`: 表面交差計算のためのメソッドタイプの名前
  * `abcorr`: 異常補正フラグ
  * `obsrvr`: 観測天体の名前
  * `dref`: 方向ベクトル `dvec` の参照フレーム
  * `dvec`: `obsrvr` からの指向方向ベクトル
  * `crdsys`: COORD を含む座標系の名前
  * `coord`: 関心のある座標の名前
  * `relate`: 極値（最大、最小、局所、絶対）を探すか、座標値と `refval` を比較する演算子
  * `refval`: 参照値
  * `adjust`: 絶対極値検索のための調整値
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔数
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfsntc_c.html)
