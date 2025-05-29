```
spkcpt(trgpos, trgctr, trgref, et, outref, refloc, abcorr, obsrvr)
```

指定された観測者に対するターゲットの状態を、指定された参照フレーム内で一定の位置を持つターゲットとして返します。ターゲットの位置は、読み込まれたSPKファイルではなく、呼び出しプログラムによって提供されます。

### 引数

  * `trgpos`: 動きの中心に対するターゲットの位置
  * `trgctr`: ターゲットの動きの中心
  * `trgref`: ターゲット位置のフレーム
  * `et`: 観測エポック
  * `outref`: 出力状態の参照フレーム
  * `refloc`: 出力参照フレーム評価の位置
  * `abcorr`: 収差補正
  * `obsrvr`: 観測エフェメリスオブジェクトの名前

### 出力

  * `state`: 観測者に対するターゲットの状態
  * `lt`: ターゲットと観測者の間の一方向の光時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcpt_c.html)
