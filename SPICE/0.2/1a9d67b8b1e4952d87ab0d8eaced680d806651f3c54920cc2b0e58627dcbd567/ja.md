```
spkw20(handle, body, center, frame, first, last, segid, intlen, n, polydg, cdata, dscale,
       tscale, initjd, initfr)
```

SPKファイルにタイプ20セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: エフェメリスオブジェクトのNAIFコード
  * `center`: 物体の運動の中心のNAIFコード
  * `frame`: 参照フレーム名
  * `first`: セグメントがカバーする間隔の開始時刻
  * `last`: セグメントがカバーする間隔の終了時刻
  * `segid`: セグメント識別子
  * `intlen`: 論理レコードがカバーする時間の長さ（日数）
  * `cdata`: チェビシェフ係数と位置の配列
  * `dscale`: データの距離スケール
  * `tscale`: データの時間スケール
  * `initjd`: 最初のレコードの開始時刻（TDBユリウス日）の整数部
  * `initfr`: 最初のレコードの開始時刻（TDBユリウス日）の小数部

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw20_c.html)
