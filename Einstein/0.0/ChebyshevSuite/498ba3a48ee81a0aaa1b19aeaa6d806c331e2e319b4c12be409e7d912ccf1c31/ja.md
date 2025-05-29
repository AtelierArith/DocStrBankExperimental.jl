```
cheb_gauss_integration_matrix([TF=Float64], n::Integer) where {TF<:AbstractFloat}
cheb_gauss_integration_matrix([TF=Float64], n::Integer, lower_bound::TF, upper_bound::TF) where {TF<:AbstractFloat}
```

`n` 個の1次チェビシェフ点での関数値を、その点での補間多項式の積分値にマッピングするチェビシェフ積分行列を計算します。最初の値はゼロであるという慣習があります。

# 参考文献

  * [chebfun/@chebcolloc1/chebcolloc1.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc1/chebcolloc1.m)
