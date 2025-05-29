```
dskxv(pri, target, srflst, et, fixref, nrays, vtxarr, dirarr)
```

複数の読み込まれたDSKセグメントによって提供されたデータを使用して、一連の光線のレイ-サーフェスインターセプトを計算します。

### 引数

  * `pri`: データ優先フラグ
  * `target`: 対象天体名
  * `srflst`: サーフェスIDリスト
  * `et`: エポック、J2000 TDBからの経過秒数で表現
  * `fixref`: 対象天体固定参照フレームの名前
  * `nrays`: 光線の数
  * `vtxarr`: 光線の頂点の配列
  * `dirarr`: 光線の方向ベクトルの配列

### 出力

  * `xptarr`: インターセプトポイント配列
  * `fndarr`: 発見フラグ配列

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskxv_c.html)
