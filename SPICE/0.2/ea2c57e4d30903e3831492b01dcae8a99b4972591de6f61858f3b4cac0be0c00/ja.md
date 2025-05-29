```
gfposc(target, frame, abcorr, obsrvr, crdsys, coord, relate, refval, adjust, step,
       nintvls, cnfine)
```

観測者-ターゲット位置ベクトルの座標が数値制約を満たす時間間隔を決定します。

### 引数

  * `target`: ターゲット天体の名前
  * `frame`: 座標計算のための基準フレームの名前
  * `abcorr`: 異常補正フラグ
  * `obsrvr`: 観測天体の名前
  * `crdsys`: `coord`を含む座標系の名前
  * `coord`: 関心のある座標の名前
  * `relate`: 極値（最大、最小、局所、絶対）を探すか、座標値とrefvalを比較する演算子
  * `refval`: 参照値
  * `adjust`: 絶対極値検索のための調整値
  * `step`: 極値と根を見つけるために使用されるステップサイズ
  * `nintvls`: ワークスペースウィンドウの間隔数
  * `cnfine`: 検索が制限されるウィンドウ

### 出力

結果を含むウィンドウを返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfposc_c.html)
