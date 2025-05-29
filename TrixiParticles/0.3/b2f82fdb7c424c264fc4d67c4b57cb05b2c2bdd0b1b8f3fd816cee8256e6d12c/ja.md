```
WendlandC2Kernel{NDIMS}()
```

Wendland C2カーネル [Wendland1995](@cite) は、コンパクトサポートを持ち、どこでも2回連続的に微分可能であるように設計された分割多項式関数です。次のように与えられます。

$$
 W(r, h) = \frac{1}{h^d} w(r/h)
$$

ここで、

$$
w(q) = \sigma \begin{cases}
    (1 - q/2)^4 (2q + 1)  & \text{if } 0 \leq q < 2, \\
    0                     & \text{if } q \geq 2,
\end{cases}
$$

$$
d
$$

は次元の数であり、$\sigma$ は次元に依存する正規化因子です。正規化因子 $\sigma$ は、2次元では $40/7\pi$、3次元では $21/2\pi$ です。

このカーネル関数は、$[0, 2h]$ のコンパクトサポートを持っています。

Wendland関数とそのSPHにおける応用についての詳細な議論は、[Dehnen (2012)](@cite Dehnen2012) を参照してください。これらの関数の滑らかさは、鋭いコーナーで詳細を失うため、最大の欠点でもあります。

スムージング長さは通常、$\delta$ が典型的な粒子間隔であるとき、$[1.2\delta, 2\delta]$ の範囲にあります。

一般的な情報と使用法については、[Smoothing Kernels](@ref smoothing_kernel) を参照してください。
