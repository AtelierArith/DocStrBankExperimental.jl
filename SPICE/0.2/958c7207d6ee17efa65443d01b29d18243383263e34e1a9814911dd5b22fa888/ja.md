```
spkcvt(trgsta, trgepc, trgctr, trgref, et, outref, refloc, abcorr, obsrvr)
```

指定された観測者に対するターゲットの状態を、指定された参照フレーム内での一定の速度で返します。ターゲットの状態は、読み込まれたSPKファイルではなく、呼び出しプログラムによって提供されます。

### 引数

  * `trgsta`: 動作の中心に対するターゲットの状態
  * `trgepc`: ターゲット状態のエポック
  * `trgctr`: ターゲットの動作の中心
  * `trgref`: ターゲット状態のフレーム
  * `et`: 観測エポック
  * `outref`: 出力状態の参照フレーム
  * `refloc`: 出力参照フレーム評価の位置
  * `abcorr`: 収差補正
  * `obsrvr`: 観測エフェメリスオブジェクトの名前

### 出力

  * `state`: 観測者に対するターゲットの状態
  * `lt`: ターゲットと観測者の間の一方向の光時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcvt_c.html)
