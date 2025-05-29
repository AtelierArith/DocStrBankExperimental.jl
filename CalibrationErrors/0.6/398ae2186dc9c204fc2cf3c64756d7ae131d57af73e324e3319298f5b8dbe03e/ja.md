```
SKCE(k; unbiased::Bool=true, blocksize=identity)
```

カーネルキャリブレーション誤差の二乗推定量 (SKCE) で、カーネル `k` を使用します。

予測とターゲットの積空間上のカーネル `k` は、予測とターゲットのタプルに対して評価できる、Julia パッケージ [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) の `Kernel` でなければなりません。

`unbiased=true` または `unbiased=false` を使用して、無偏または偏りのあるバリアントを選択できます（詳細は以下を参照）。

SKCE は、異なるサンプルのブロックの平均推定値として推定されます。ブロックごとのサンプル数は `blocksize` によって設定されます：

  * `blocksize` が関数 `blocksize(n::Int)` の場合、ブロックごとのサンプル数は `blocksize(n)` に設定され、ここで `n` はサンプルの総数です。
  * `blocksize` が整数の場合、ブロックごとのサンプル数は `blocksize` に設定され、サンプルの総数には依存しません。

デフォルト設定 `blocksize=identity` は、すべてのサンプルを含む単一のブロックが使用されることを意味します。

ブロックごとのサンプル数は、`unbiased=false` の場合は少なくとも 1 でなければならず、`unbiased=true` の場合は 2 でなければなりません。さらに、サンプルの総数を超えてはなりません。最後のブロックが不完全な場合は無視されることに注意してください（詳細は以下を参照）。

# 詳細

無偏推定量は非負であることが保証されていませんが、偏りのある推定量は常に非負です。

推定量のサンプルの複雑さは $O(mn)$ であり、ここで $m$ はブロックサイズ、$n$ はサンプルの総数です。特に、デフォルト設定 `blocksize=identity` の場合、推定量は二次のサンプルの複雑さを持ちます。

データセット $(P_{X_i}, Y_i)_{i=1,\ldots,n}$ を予測と対応するターゲットとします。ブロックサイズ $m$ の推定量は次のように定義されます。

$$
{\bigg\lfloor \frac{n}{m} \bigg\rfloor}^{-1} \sum_{b=1}^{\lfloor n/m \rfloor}
|B_b|^{-1} \sum_{(i, j) \in B_b} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

ここで

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big)
\end{aligned}
$$

およびブロック $B_b$ ($b = 1, \ldots, \lfloor n/m \rfloor$) は次のように定義されます。

$$
B_b = \begin{cases}
\{(i, j): (b - 1) m < i < j \leq bm \} & \text{(無偏)}, \\
\{(i, j): (b - 1) m < i, j \leq bm \} & \text{(偏りあり)}.
\end{cases}
$$

# 参考文献

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [多クラス分類におけるキャリブレーションテスト：統一フレームワーク](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [分類を超えたキャリブレーションテスト](https://openreview.net/forum?id=-bxf89v3Nx).
