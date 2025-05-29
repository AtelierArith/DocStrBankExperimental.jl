```
SchoenbergCubicSplineKernel{NDIMS}()
```

シューベルトの三次スプラインカーネル [Schoenberg (1946)](@cite Schoenberg1946) によって与えられます。

$$
    W(r, h) = \frac{1}{h^d} w(r/h)
$$

ここで

$$
w(q) = \sigma \begin{cases}
    \frac{1}{4} (2 - q)^3 - (1 - q)^3   & \text{if } 0 \leq q < 1, \\
    \frac{1}{4} (2 - q)^3               & \text{if } 1 \leq q < 2, \\
    0                                   & \text{if } q \geq 2, \\
\end{cases}
$$

$$
d
$$

は次元の数で、$\sigma$ は次元 $[1, 2, 3]$ における正規化定数で、$\sigma =[\frac{2}{3}, \frac{10}{7 \pi}, \frac{1}{\pi}]$ です。

このカーネル関数は $[0, 2h]$ のコンパクトサポートを持ちます。

シューベルトの三次、四次、五次スプラインカーネルの正規化因子を含む概要については、[Price (2012)](@cite Price2012) を参照してください。高次のシューベルトカーネルの解析的な公式については、[Monaghan (1985)](@cite Monaghan1985) を参照してください。シューベルトスプラインカーネルの最大の欠点は、他のカーネルのバリアントと比較してノイズが増加する可能性のある、かなり滑らかでない一次導関数です。

スムージング長は通常 $[1.1\delta, 1.3\delta]$ の範囲にあり、ここで $\delta$ は典型的な粒子間隔です。

一般的な情報と使用法については、[Smoothing Kernels](@ref smoothing_kernel) を参照してください。
