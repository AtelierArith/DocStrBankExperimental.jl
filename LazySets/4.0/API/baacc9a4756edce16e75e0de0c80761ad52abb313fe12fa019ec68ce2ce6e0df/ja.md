```
affine_map(M::AbstractMatrix, X::LazySet, v::AbstractVector)
```

アフィン写像 $M · X + v$ を計算します。

### 入力

  * `M` – 行列
  * `X` – 集合
  * `v` – 平行移動ベクトル

### 出力

アフィン写像 $M · X + v$ を表す集合。
