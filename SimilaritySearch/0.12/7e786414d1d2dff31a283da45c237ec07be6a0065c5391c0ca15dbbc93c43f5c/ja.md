```
distsample_ut(dist::SemiMetric, X::AbstractDatabase; prob=0.01, samplesize=0)
distsample(dist::SemiMetric, X::AbstractDatabase; prob=0.01, samplesize=sqrt(|X|))

上三角対距離行列のサンプルを計算します。
サイズが ``n`` のデータベースに対して、``prob * n^2/2`` エントリに近い距離の配列を返します。
このメソッドは小さなデータセット（百万サイズのデータセットではない）で動作するのに適しています。このメソッドは重複や対称重複を返しません。

- `dist`: 距離関数
- `X`: 入力データベース
- `prob`: サンプリング確率（上三角対距離行列において）
- `samplesize`: samplesize が指定されている場合、指定された確率を無視し、`samplesize` に近い値を達成するために必要な `prob` を計算します
```
