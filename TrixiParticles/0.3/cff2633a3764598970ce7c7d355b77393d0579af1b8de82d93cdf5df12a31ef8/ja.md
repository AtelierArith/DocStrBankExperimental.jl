```
WendlandC4Kernel{NDIMS}()
```

Wendland C4 カーネル [Wendland1995](@cite) は、コンパクトサポートを持ち、どこでも4回連続的に微分可能であるように設計された分割多項式関数です。次のように与えられます。

$$
 W(r, h) = \frac{1}{h^d} w(r/h)
$$

ここで、

$$
w(q) = \sigma \begin{cases}
    (1 - q/2)^6 (35q^2 / 12 + 3q + 1)   & \text{if } 0 \leq q < 2, \\
    0                                   & \text{if } q \geq 2,
\end{cases}
$$

$$
d
$$

は次元の数で、$\sigma$ は次元に依存する正規化因子です。正規化因子 $\sigma$ は、2次元では $9 / \pi$、3次元では $495 / 32\pi$ です。

このカーネル関数は、$[0, 2h]$ のコンパクトサポートを持っています。

Wendland 関数とその SPH における応用についての詳細な議論は、[Dehnen (2012)](@cite Dehnen2012) を参照してください。これらの関数の滑らかさは、鋭いコーナーで詳細を失うため、最大の欠点でもあります。

スムージング長さは通常、$[1.5\delta, 2.3\delta]$ の範囲にあり、ここで $\delta$ は典型的な粒子間隔です。

一般的な情報と使用法については、[Smoothing Kernels](@ref smoothing_kernel) を参照してください。
