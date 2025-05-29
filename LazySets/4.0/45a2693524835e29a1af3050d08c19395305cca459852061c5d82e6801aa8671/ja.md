```
QuadraticMap{N, S<:LazySet{N}, MVT<:AbstractVector{<:AbstractMatrix{N}}} <: LazySet{N}
```

集合の二次写像を表す型。

### フィールド

  * `Q` – 行列
  * `X` – 集合

### ノート

$$
n
$$

個の正方行列 $Q^{(i)}$ によって与えられる集合 $X$ の二次写像は次のように定義されます。

$$
\left\{ λ \mid λ_i = x^T Q^{(i)} x,~i = 1, …, n,~x ∈ X \right\}
$$

ここで、各座標 $i$ は $i$ 番目の行列 $Q^{(i)}$ によって影響を受けます。
