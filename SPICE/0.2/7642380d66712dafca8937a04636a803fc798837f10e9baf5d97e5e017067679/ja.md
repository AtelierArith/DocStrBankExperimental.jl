```
spkw08(handle, body, center, frame, first, last, segid, degree, states, epoch1, step)
```

SPKファイルにタイプ8セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: 軌道対象の天体コード
  * `center`: 天体の運動の中心の天体コード
  * `frame`: 状態の基準フレーム
  * `first`: 状態を計算できる最初の有効時間
  * `last`: 状態を計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `degree`: 補間多項式の次数
  * `states`: 状態
  * `epoch1`: 状態配列の最初の状態のエポック
  * `step`: 状態のエポックを分ける時間ステップ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw08_c.html)
