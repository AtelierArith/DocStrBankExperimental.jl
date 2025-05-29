```
τ = time_constant(g)
```

順序 (0, 1) または順序 (0, 2) の伝達関数の時間定数 τ を計算します。

順序 (0, 1) の表現:

$$
g(s)=\frac{K}{\tau s+1}
$$

順序 (0, 2) の表現:

$$
g(s)=\frac{K}{\tau^2 s^2 + 2\tau \xi s +1}
$$

# 戻り値

`τ::Float64`: 時間定数。

# 例

```jldoctest
g = 4 / (6 * s + 2)
time_constant(g)
# 出力 
3.0

g = 1.0 / (8 * s^2 + 0.8 * s + 2)
time_constant(g) 
# 出力
2.0
```
