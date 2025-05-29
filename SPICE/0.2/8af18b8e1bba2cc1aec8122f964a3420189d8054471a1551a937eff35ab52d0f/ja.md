```
dskw02(handle, center, surfid, dclass, frame, corsys, corpar, mncor1, mxcor1,
       mncor2, mxcor2, mncor3, mxcor3, first, last, vrtces, plates, spaixd, spaixi)
```

DSKファイルにタイプ2セグメントを書き込みます。

### 引数

  * `handle`: 開かれたDSKファイルに割り当てられたハンドル
  * `center`: 中心天体のIDコード
  * `surfid`: 表面IDコード
  * `dclass`: データクラス
  * `frame`: 参照フレーム
  * `corsys`: 座標系コード
  * `corpar`: 座標系パラメータ
  * `mncor1`: 最小値の第一座標
  * `mxcor1`: 最大値の第一座標
  * `mncor2`: 最小値の第二座標
  * `mxcor2`: 最大値の第二座標
  * `mncor3`: 最小値の第三座標
  * `mxcor3`: 最大値の第三座標
  * `first`: カバレッジ開始時間
  * `last`: カバレッジ停止時間
  * `nv`: 頂点の数
  * `vrtces`: 頂点
  * `np`: プレートの数
  * `plates`: プレート
  * `spaixd`: 空間インデックスの倍精度成分
  * `spaixi`: 空間インデックスの整数成分

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskw02_c.html)
