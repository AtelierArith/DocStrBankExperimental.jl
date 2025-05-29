```
spkw12(handle, body, center, frame, first, last, segid, degree, states, epoch1, step)
```

SPKファイルにタイプ12セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: エフェメリスオブジェクトのボディコード
  * `center`: ボディの運動の中心のボディコード
  * `frame`: ステートの基準フレーム
  * `first`: ステートを計算できる最初の有効時間
  * `last`: ステートを計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `degree`: 補間多項式の次数
  * `states`: ステート
  * `epoch1`: ステート配列の最初のステートのエポック
  * `step`: ステートのエポックを分ける時間ステップ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw12_c.html)
