```
BlockUnbiasedSKCE(k[, blocksize = 2])
```

カーネル `k` を使用した二乗カーネルキャリブレーションエラー (SKCE) の無偏推定量で、`blocksize` サンプルのブロックを使用します。

予測とターゲットの積空間上のカーネル `k` は、予測とターゲットのタプルに対して評価できる [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) の `Kernel` でなければなりません。

ブロックごとのサンプル数は、少なくとも 2 以上、かつ総サンプル数以下でなければなりません。最後のブロックのサンプルが不完全な場合は、そのサンプルは破棄されることに注意してください（詳細は以下を参照）。

# 詳細

この推定量は無偏であり、非負であることは保証されていません。そのサンプルの複雑さは $O(Bn)$ であり、ここで $B$ はブロックサイズ、$n$ は総サンプル数です。

$$
(P_{X_i}, Y_i)_{i=1,\ldots,n}
$$

を予測と対応するターゲットのデータセットとします。ブロックサイズ $B$ の推定量は次のように定義されます。

$$
{\bigg\lfloor \frac{n}{B} \bigg\rfloor}^{-1} \sum_{b=1}^{\lfloor n/B \rfloor}
\frac{2}{B(B-1)} \sum_{(b - 1) B < i < j \leq bB} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
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

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [多クラス分類におけるキャリブレーションテスト: 統一フレームワーク](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [分類を超えたキャリブレーションテスト](https://openreview.net/forum?id=-bxf89v3Nx).

また、[`BiasedSKCE`](@ref)、[`UnbiasedSKCE`](@ref) も参照してください。
