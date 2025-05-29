```
cheb_series_integration_matrix([TR=Float64], n::Integer) where {TR<:AbstractFloat}
cheb_series_integration_matrix([TR=Float64], n::Integer, lower_bound::TR, upper_bound::TR) where {TR<:AbstractFloat}
```

チェビシェフ係数の積分行列を生成し、チェビシェフ係数を補間多項式の積分の係数にマッピングします。

# 引数

  * `TR`: 行列要素の型パラメータ（例：Float64）
  * `n`: 行列のサイズ（n×n）
  * `lower_bound`: （オプション）積分区間の下限
  * `upper_bound`: （オプション）積分区間の上限

# 参考文献

  * [chebfun/@chebcolloc1/chebcolloc1.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc1/chebcolloc1.m)
  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)
