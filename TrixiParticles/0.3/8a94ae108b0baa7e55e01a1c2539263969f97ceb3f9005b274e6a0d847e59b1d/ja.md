```
SchoenbergQuarticSplineKernel{NDIMS}()
```

Schoenbergによる四次スプラインカーネル（1946年）[@cite Schoenberg1946]は、次のように与えられます。

$$
    W(r, h) = \frac{1}{h^d} w(r/h)
$$

ここで、

$$
w(q) = \sigma \begin{cases}
    \left(5/2 - q \right)^4 - 5\left(3/2 - q \right)^4
    + 10\left(1/2 - q \right)^4 & \text{if } 0 \leq q < \frac{1}{2}, \\
    \left(5/2 - q \right)^4 - 5\left(3/2 - q \right)^4
    & \text{if } \frac{1}{2} \leq q < \frac{3}{2}, \\
    \left(5/2 - q \right)^4 & \text{if } \frac{3}{2} \leq q < \frac{5}{2}, \\
    0 & \text{if } q \geq \frac{5}{2},
\end{cases}
$$

ここで、$d$は次元の数であり、$\sigma$は次のように与えられる正規化定数です：$\sigma =[\frac{1}{24}, \frac{96}{1199 \pi}, \frac{1}{20\pi}]$（1, 2, 3次元の場合）。

このカーネル関数は、$[0, 2.5h]$のコンパクトサポートを持ちます。

正規化因子を含むSchoenbergの三次、四次、五次スプラインカーネルの概要については、[Price (2012)](@cite Price2012)を参照してください。高次のSchoenbergカーネルの解析的な公式については、[Monaghan (1985)](@cite Monaghan1985)を参照してください。

Schoenbergスプラインカーネルの最大の欠点は、他のカーネルバリアントと比較してノイズが増加する可能性のある、かなり滑らかでない一次導関数です。

スムージング長は通常、$[1.1\delta, 1.5\delta]$の範囲にあり、ここで$\delta$は典型的な粒子間隔です。

一般的な情報と使用法については、[Smoothing Kernels](@ref smoothing_kernel)を参照してください。
