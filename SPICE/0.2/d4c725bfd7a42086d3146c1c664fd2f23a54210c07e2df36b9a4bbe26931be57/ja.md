```
spkw03(handle, body, center, frame, first, last, segid, intlen, cdata, btime)
```

SPKファイルにタイプ3セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: 軌道対象のボディコード
  * `center`: ボディの運動の中心のボディコード
  * `frame`: 状態の基準フレーム
  * `first`: 状態を計算できる最初の有効時間
  * `last`: 状態を計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `intlen`: 論理レコードがカバーする時間の長さ
  * `cdata`: チェビシェフ係数の配列
  * `btime`: 最初の論理レコードの開始時間

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw03_c.html)
