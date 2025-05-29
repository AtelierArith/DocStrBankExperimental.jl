```
spkuds(descr)
```

SPKセグメント記述子の内容を展開します。

### 引数

  * `descr`: SPKセグメント記述子

### 出力

  * `body`: セグメントの天体のNAIF IDコード
  * `center`: 天体の運動の中心
  * `frame`: このセグメントのフレームのIDコード
  * `type`: SPKセグメントのタイプ
  * `first`: セグメントが有効な最初の時刻
  * `last`: セグメントが有効な最後の時刻
  * `start`: セグメントの開始DAFアドレス
  * `stop`: セグメントの終了DAFアドレス

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spkuds_c.html)
