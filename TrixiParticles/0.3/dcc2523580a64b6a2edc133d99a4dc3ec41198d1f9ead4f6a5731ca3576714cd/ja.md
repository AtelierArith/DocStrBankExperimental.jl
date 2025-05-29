```
SchoenbergQuinticSplineKernel{NDIMS}()
```

クインティックスプラインカーネルは、[Schoenberg (1946)](@cite Schoenberg1946)によって与えられます。

$$
    W(r, h) = \frac{1}{h^d} w(r/h)
$$

ここで、

$$
w(q) = \sigma \begin{cases}
    (3 - q)^5 - 6(2 - q)^5 + 15(1 - q)^5    & \text{if } 0 \leq q < 1, \\
    (3 - q)^5 - 6(2 - q)^5                  & \text{if } 1 \leq q < 2, \\
    (3 - q)^5                               & \text{if } 2 \leq q < 3, \\
    0                                       & \text{if } q \geq 3,
\end{cases}
$$

ここで、$d$は次元の数であり、$\sigma$は次元$[1, 2, 3]$における正規化定数で、$\sigma =[\frac{1}{120}, \frac{7}{478 \pi}, \frac{1}{120\pi}]$です。

このカーネル関数は、$[0, 3h]$のコンパクトサポートを持ちます。

正規化因子を含むSchoenbergの三次、四次、五次スプラインカーネルの概要については、[Price (2012)](@cite Price2012)を参照してください。高次のSchoenbergカーネルの解析的な公式については、[Monaghan (1985)](@cite Monaghan1985)を参照してください。

Schoenbergスプラインカーネルの最大の欠点は、他のカーネルバリアントと比較してノイズが増加する可能性のある、かなり滑らかでない一次導関数です。

スムージング長は通常、$[1.1\delta, 1.5\delta]$の範囲にあり、ここで$\delta$は典型的な粒子間隔です。

一般的な情報と使用法については、[Smoothing Kernels](@ref smoothing_kernel)を参照してください。
