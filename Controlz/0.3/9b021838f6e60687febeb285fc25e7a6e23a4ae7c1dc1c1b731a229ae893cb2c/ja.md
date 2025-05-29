```
g = second_order_system(K, τ, ξ)
```

`K`、時間定数 `τ`、および減衰係数 `ξ` を持つ二次伝達関数を構築します：

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# 例

```jldoctest
K = 1.0
τ = 2.0
ξ = 0.1
g = second_order_system(K, τ, ξ)
# 出力
         1.0
---------------------
4.0*s^2 + 0.4*s + 1.0
```

# 戻り値

  * `g::TransferFunction`: 二次伝達関数。そう、(0, 2) 次。
