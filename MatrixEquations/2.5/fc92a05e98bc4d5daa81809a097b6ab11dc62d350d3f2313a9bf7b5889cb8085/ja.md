```
sep = opsepest(opinv; exact = false)
```

`op`という線形演算子の`1`-ノルム分離の推定値`sep`を計算します。ここで、`opinv`は逆演算子`inv(op)`です。この推定値は、`exact = false`の場合は`1 / \|opinv\|_1`として計算され、`exact = true`の場合は`1`-ノルムの計算された正確な値が使用されます。`exact = true`オプションは、大きな次数の演算子には推奨されません。

演算子`op`の分離は次のように定義されます。

$$
\text{sep} = \displaystyle\min_{X\neq 0} \frac{\|op*X\|}{\|X\|}.
$$

演算子`op`の逆条件数の推定値は、$\text{sep}/\|op\|_1$として計算できます。

# 例

```jldoctest
julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> opsepest(invlyapop(A))
0.26548672566371656

julia> 1/opnorm1est(invlyapop(A))
0.26548672566371656

julia> opsepest(invlyapop(A),exact = true)
0.26548672566371656

julia> 1/opnorm1(invlyapop(A))
0.26548672566371656
```
