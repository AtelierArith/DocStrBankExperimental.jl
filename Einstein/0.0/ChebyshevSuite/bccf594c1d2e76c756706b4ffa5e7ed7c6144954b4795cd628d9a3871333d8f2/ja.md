```
cheb_lobatto_differentiation_matrix([TR=Float64], n::Integer, k::Integer=1) where {TR<:AbstractFloat}
```

2次のチェビシェフ点での関数値を、その点での補間多項式の`k`-次導関数の値にマッピングするチェビシェフ微分行列を構築します。

# 引数

  * `TR`: 要素タイプ（デフォルトはFloat64）
  * `n::Integer`: チェビシェフ点の数
  * `k::Integer=1`: 導関数の次数（デフォルト: 1）

# 参考文献

  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)

```
