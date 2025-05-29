```
ξ = damping_coefficient(g)
```

順序 (0, 2) の伝達関数の減衰係数 ξ を計算します。

順序 (0, 2) の表現：

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# 戻り値

`ξ::Float64`: 減衰係数

# 例

```jldoctest
g = 1.0 / (8 * s^2 + 0.8 * s + 2)
damping_coefficient(g)
# 出力
0.1
```
