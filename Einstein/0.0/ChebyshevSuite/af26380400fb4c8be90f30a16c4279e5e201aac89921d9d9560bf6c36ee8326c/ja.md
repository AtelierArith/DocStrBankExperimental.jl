```
cheb_lobatto_integration_matrix([TF=Float64], n::Integer) where {TF<:AbstractFloat}
cheb_lobatto_integration_matrix([TF=Float64], n::Integer, lower_bound::TF, upper_bound::TF) where {TF<:AbstractFloat}
```

`n`個の2次のチェビシェフ点での関数値を、その点での補間多項式の積分値にマッピングするチェビシェフ積分行列を計算します。最初の値はゼロであるという慣習に従います。

# 参考文献

  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)
