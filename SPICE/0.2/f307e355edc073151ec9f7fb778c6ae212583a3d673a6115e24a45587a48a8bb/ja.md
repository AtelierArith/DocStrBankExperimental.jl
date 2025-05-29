```
spkpds(body, center, frame, typ, first, last)
```

ルーチンエラーチェックを実行し、すべてのチェックが通過した場合、SPKセグメントの記述子をパックします。

### 引数

  * `body`: セグメントの天体のNAIF IDコード
  * `center`: 天体の運動の中心
  * `frame`: このセグメントのフレーム
  * `type`: 作成するSPKセグメントのタイプ
  * `first`: セグメントが有効な最初のエポック
  * `last`: セグメントが有効な最後のエポック

### 出力

SPKセグメント記述子を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkpds_c.html)
