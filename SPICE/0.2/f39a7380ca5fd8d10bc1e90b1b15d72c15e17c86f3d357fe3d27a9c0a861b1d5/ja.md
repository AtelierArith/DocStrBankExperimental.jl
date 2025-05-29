```
spkw05(handle, body, center, frame, first, last, segid, gm, states, epochs)
```

時間順に並べられた離散状態とエポック、および中心天体の重力パラメータを用いて、タイプ5のSPKセグメントを作成します。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: エフェメリスオブジェクトのボディコード
  * `center`: そのボディの運動の中心のボディコード
  * `frame`: 状態の参照フレーム
  * `first`: 状態を計算できる最初の有効時間
  * `last`: 状態を計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `gm`: 中心天体の重力パラメータ
  * `states`: 状態
  * `epochs`: エポック

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw05_c.html)
