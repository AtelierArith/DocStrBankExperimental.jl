```
decompose(S::LazySet, block_options; [block_size]::Int=1)
```

高次元集合を均一なサイズの部分空間に対する射影のオーバー近似の直積に分解します。

### 入力

  * `S`             – 集合
  * `block_options` – オーバー近似オプションまたはブロックインデックスから対応するオーバー近似オプションへのマッピング
  * `block_size`    – （オプション; デフォルト: `1`）ブロックのサイズ

### 出力

低次元の近似射影を含む `CartesianProductArray`。
