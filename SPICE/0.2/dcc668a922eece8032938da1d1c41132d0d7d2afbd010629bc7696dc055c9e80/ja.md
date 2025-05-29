```
spkw10(handle, body, center, frame, first, last, segid, consts, elems, epochs)
```

SPKファイルにタイプ10セグメントを書き込みます。

### 引数

  * `handle`: 書き込み用に開かれたDAFファイルのハンドル
  * `body`: セグメントの天体のNAIF IDコード
  * `center`: 天体の運動の中心
  * `frame`: このセグメントの基準フレーム
  * `first`: セグメントが有効な最初のエポック
  * `last`: セグメントが有効な最後のエポック
  * `segid`: セグメント識別子に使用する文字列
  * `consts`: セグメントのための地球物理定数の配列
  * `elems`: "二行"要素セットのコレクション
  * `epochs`: 要素セットに関連付けられたエポック

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkw10_c.html)
