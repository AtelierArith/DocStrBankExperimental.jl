```
linear_map(M::AbstractMatrix, tr::Translation)
```

平行移動の具体的な線形写像。

### 入力

  * `M`  – 行列
  * `tr` – 一つの集合の平行移動

### 出力

線形写像に対応する具体的な集合。結果の型は、`tr` にラップされた集合の型に依存します。

### アルゴリズム

`affine_map(M, tr.X, M * tr.v)` を計算します。
