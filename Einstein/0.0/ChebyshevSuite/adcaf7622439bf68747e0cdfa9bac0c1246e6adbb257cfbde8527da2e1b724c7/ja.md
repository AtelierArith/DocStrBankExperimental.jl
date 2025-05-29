```
cheb_lobatto_angles(TF, n) where {TF<:AbstractFloat}
```

2次のチェビシェフ点の角度を計算します：

$$
\theta_k = \frac{k\pi}{n-1}, \quad k = n-1,\ldots,0
$$

# 引数

  * `TF`: 角度の型パラメータ（例：Float64）
  * `n`: 点の数
