```
cheb_gauss_points([TF=Float64], n::Integer) where {TF<:AbstractFloat}
cheb_gauss_points([TF=Float64], n::Integer, lower_bound::TF, upper_bound::TF) where {TF<:AbstractFloat}
```

2次のチェビシェフ点を生成します。

標準区間 [-1,1] の場合:

$$
x_k = -\cos\left(\frac{(2k + 1)\pi}{2n}\right), \quad k = 0,1,\ldots,n-1
$$

マッピングされた区間 [lower*bound,upper*bound] の場合:

$$
x_{\mathrm{mapped}} = \frac{x_{\mathrm{max}} + x_{\mathrm{min}}}{2} + \frac{x_{\mathrm{min}} - x_{\mathrm{max}}}{2}x_k
$$

# 引数

  * `TF`: グリッドポイントの型パラメータ（例: Float64）
  * `n`: 点の数
  * `lower_bound`: （オプション）マッピングされた区間の下限
  * `upper_bound`: （オプション）マッピングされた区間の上限

# 参考文献

  * [chebfun/@chebtech1/chebpts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech1/chebpts.m)

```
