```
poisson_rand([rng = default_rng()], ::Type{T}, dwell_time, []) → T
```

次の状態に留まるステップのランダムな数を生成します。

# 追加情報

RTN信号が現在の状態に時間 $t \in (t_0, t_0 + {\rm d} t)$ 留まる確率は次のように与えられます。

$$
{\rm Pr}\left( t \in (t_0, t_0 + {\rm d} t) \right) = {\rm e}^{-t/T_D} \cdot \frac{{\rm d}t}{T_D}.
$$

次に、この確率分布から*逆CDF*法を使用してサンプリングを行い、次のように得られます。

$$
t \approx {\rm floor} \left[ -T_D \ln \left( 1 - u \right)  \right],
$$

ここで、$u \in (0, 1)$ は `rand()` によって生成された一様ランダムな `Float` です。この近似は、$t$ が時系列における離散時間を表すために必要です。
