```
spkcpo(target, et, outref, refloc, abcorr, obspos, obsctr, obsref)
```

指定されたターゲットの状態を「観測者」に対して返します。観測者は指定された参照フレーム内で一定の位置を持っています。観測者の位置は、読み込まれたSPKファイルではなく、呼び出しプログラムによって提供されます。

### 引数

  * `target`: ターゲットのエフェメリスオブジェクトの名前
  * `et`: 観測エポック
  * `outref`: 出力状態の参照フレーム
  * `refloc`: 出力参照フレーム評価の位置
  * `abcorr`: 収差補正
  * `obspos`: 動きの中心に対する観測者の位置
  * `obsctr`: 観測者の動きの中心
  * `obsref`: 観測者位置のフレーム

### 出力

  * `state`: 観測者に対するターゲットの状態
  * `lt`: ターゲットと観測者の間の一方向の光時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkcpo_c.html)

```
