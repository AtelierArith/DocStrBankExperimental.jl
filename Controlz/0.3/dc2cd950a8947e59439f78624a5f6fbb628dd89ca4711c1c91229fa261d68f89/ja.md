```
g = first_order_system(K, τ)
```

ゲイン `K` と時間定数 `τ` を持つ一次伝達関数を構築します：

$$
g(s)=\frac{K}{\tau s+1}
$$

# 例

```jldoctest
K = 1.0
τ = 3.0
g = first_order_system(K, τ)
# 出力
    1.0
-----------
3.0*s + 1.0
```

# 戻り値

  * `g::TransferFunction`: 一次伝達関数。まあ、(0, 1) 次。
