```
UnbiasedSKCE(k)
```

カーネル `k` に対する二乗カーネルキャリブレーション誤差 (SKCE) の無偏推定量。

予測とターゲットの積空間上のカーネル `k` は、予測とターゲットのタプルに対して評価可能な、Julia パッケージ [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) の `Kernel` でなければなりません。

# 詳細

この推定量は無偏であり、非負であることは保証されていません。そのサンプルの複雑さは $O(n^2)$ であり、ここで $n$ はサンプルの総数です。

データセット $(P_{X_i}, Y_i)_{i=1,\ldots,n}$ を予測と対応するターゲットの組とします。この推定量は次のように定義されます。

$$
\frac{2}{n(n-1)} \sum_{1 \leq i < j \leq n} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

ここで

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big).
\end{aligned}
$$

# 参考文献

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [Calibration tests in multi-class classification: A unifying framework](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx).

参照: [`BiasedSKCE`](@ref), [`BlockUnbiasedSKCE`](@ref)
