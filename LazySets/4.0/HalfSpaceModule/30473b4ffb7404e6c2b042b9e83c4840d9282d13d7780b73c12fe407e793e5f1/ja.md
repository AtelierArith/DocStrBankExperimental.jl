```
halfspace_right(p::AbstractVector, q::AbstractVector)
```

2次元の線分を2つの点を通して「右側」を記述する半空間を返します。

### 入力

  * `p` – 最初の点
  * `q` – 2番目の点

### 出力

2つの点 `p` と `q` を通る境界を持ち、指向された線分 `pq` の右側を記述する半空間。

### アルゴリズム

[`halfspace_left`](@ref) のドキュメントを参照してください。
