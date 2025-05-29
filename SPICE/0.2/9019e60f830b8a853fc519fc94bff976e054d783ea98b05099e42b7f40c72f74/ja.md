```
spkw17(handle, body, center, frame, first, last, segid, epoch, eqel, rapol, decpol)
```

SPKファイルにタイプ17セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `body`: 軌道対象の天体コード
  * `center`: 天体の運動の中心の天体コード
  * `frame`: 状態の基準フレーム
  * `first`: 状態を計算できる最初の有効時間
  * `last`: 状態を計算できる最後の有効時間
  * `segid`: セグメント識別子
  * `epoch`: J2000からの秒数での要素のエポック
  * `eqel`: 等分点要素の配列
  * `rapol`: 基準平面の極の赤経
  * `decpol`: 基準平面の極の赤緯

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw17_c.html)
