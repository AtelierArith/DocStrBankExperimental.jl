```
BiasedSKCE(k)
```

カーネル `k` を用いた二乗カーネルキャリブレーション誤差 (SKCE) のバイアス推定量。

予測とターゲットの積空間上のカーネル `k` は、予測とターゲットのタプルに対して評価可能な、Juliaパッケージ [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) の `Kernel` でなければなりません。

# 詳細

この推定量はバイアスがあり、非負であることが保証されています。そのサンプルの複雑さは $O(n^2)$ であり、ここで $n$ はサンプルの総数です。

データセット $(P_{X_i}, Y_i)_{i=1,\ldots,n}$ を予測と対応するターゲットとします。この推定量は次のように定義されます。

$$
\frac{1}{n^2} \sum_{i,j=1}^n h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big)
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

推定量のバイアスは次のようになります。

$$
\frac{1}{n} \Big(\mathbb{E}_{P_X,Y} h_k\big((P_X, Y), (P_X, Y)\big) - \mathrm{SKCE}_k\Big).
$$

# 参考文献

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [多クラス分類におけるキャリブレーションテスト: 統一フレームワーク](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [分類を超えたキャリブレーションテスト](https://openreview.net/forum?id=-bxf89v3Nx).

また、[`UnbiasedSKCE`](@ref)、[`BlockUnbiasedSKCE`](@ref) も参照してください。
