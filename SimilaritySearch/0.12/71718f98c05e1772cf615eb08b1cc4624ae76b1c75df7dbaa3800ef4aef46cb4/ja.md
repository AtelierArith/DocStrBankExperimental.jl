```
distsample(dist::SemiMetric, X::AbstractDatabase; samplesize=sqrt(|X|))

ペアワイズ距離行列のサンプルを計算します。
サイズ`samplesize`の配列を返します。

- `dist`: 距離関数
- `X`: 入力データベース
- `samplesize`: サンプルのサイズ
```
