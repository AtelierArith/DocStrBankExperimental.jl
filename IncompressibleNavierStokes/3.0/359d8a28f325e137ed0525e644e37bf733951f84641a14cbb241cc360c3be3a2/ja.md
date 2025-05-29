```julia
stretched_grid(a, b, N) -> Any
stretched_grid(a, b, N, s) -> Any

```

`a`から`b`までの`N + 1`点の非均一グリッドを、伸縮因子`s`を用いて作成します。`s = 1`の場合は、`a`から`b`までの均一な間隔を返します。それ以外の場合、$x \in \mathbb{R}^{N + 1}$となるベクトルを返します。ここで、$x_n = a + \sum_{i = 1}^n s^{i - 1} h$（$n = 0, \dots , N$）です。$x_N = b$と設定すると、$h = (b - a) \frac{1 - s}{1 - s^N}$となり、次のようになります。

$$
x_n = a + (b - a) \frac{1 - s^n}{1 - s^N}, \quad n = 0, \dots, N.
$$

`stretched_grid(a, b, N, s)[n]`は$x_{n - 1}$に対応します。

他に[`cosine_grid`](@ref)も参照してください。
