```
qdq2av(q, dq)
```

単位クォータニオンとその時間に関する導関数から角速度を導出します。

### 引数

  * `q`: 単位SPICEクォータニオン（4つの要素を持つ任意の反復可能なオブジェクト）
  * `dq`: 時間に関する`q`の導関数

### 出力

`q`と`dq`によって定義される角速度ベクトル

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/qdq2av_c.html)
