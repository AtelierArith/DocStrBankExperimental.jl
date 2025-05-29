```
cheb_gauss_angles(TF, n) where {TF<:AbstractFloat}
```

1次のチェビシェフ点の角度を計算します：

$$
\theta_k = \frac{(2k + 1)\pi}{2n}, \quad k = n-1,\ldots,0
$$

# 引数

  * `TF`: 角度の型パラメータ（例：Float64）
  * `n`: 点の数
