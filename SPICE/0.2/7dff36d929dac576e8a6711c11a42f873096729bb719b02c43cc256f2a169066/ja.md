```
spk14b(handle, segid, body, center, frame, first, last, chbdeg)
```

`handle`に関連付けられたSPKファイルでタイプ14のSPKセグメントを開始します。 [`spk14a`](@ref)および[`spk14e`](@ref)も参照してください。

### 引数

  * `handle`: 書き込み用に開かれたSPKファイルのハンドル
  * `segid`: セグメント識別子として使用する文字列
  * `body`: セグメントの天体のNAIF IDコード
  * `center`: 天体の運動の中心
  * `frame`: このセグメントの基準フレーム
  * `first`: セグメントが有効な最初のエポック
  * `last`: セグメントが有効な最後のエポック
  * `chbdeg`: 使用されるチェビシェフ多項式の次数

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spk14b_c.html)
