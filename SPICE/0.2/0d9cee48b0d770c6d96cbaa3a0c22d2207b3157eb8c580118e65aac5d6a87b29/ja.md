```
spkw18(handle, subtyp, body, center, frame, first, last, segid, degree, packts, epochs)
```

SPKファイルにタイプ18セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `subtyp`: SPKタイプ18のサブタイプコード、`:S18TP0`または`:S18TP1`
  * `body`: エフェメリスオブジェクトのNAIFコード
  * `center`: 物体の運動の中心のNAIFコード
  * `frame`: 参照フレーム名
  * `first`: セグメントがカバーする間隔の開始時刻
  * `last`: セグメントがカバーする間隔の終了時刻
  * `segid`: セグメント識別子
  * `degree`: 補間多項式の次数
  * `packts`: 物体の幾何学的状態を表すデータパケットの時間順配列

      * `:S18TP0`の場合: `[x,  y,  z,  dx/dt,  dy/dt,  dz/dt, vx, vy, vz, dvx/dt, dvy/dt, dvz/dt]`
      * `:S18TP1`の場合: `[x,  y,  z,  dx/dt,  dy/dt,  dz/dt]`
  * `epochs`: 状態に対応するエポックの配列。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw18_c.html)
