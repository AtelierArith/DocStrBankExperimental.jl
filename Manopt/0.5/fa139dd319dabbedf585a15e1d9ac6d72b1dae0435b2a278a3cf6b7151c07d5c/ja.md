```
AdaptiveWNGradient(; kwargs...)
AdaptiveWNGradient(M::AbstractManifold; kwargs...)
```

[GrapigliaStella:2023](@cite)によって導入された適応勾配法に基づくステップサイズ。

正の閾値 $\hat{c} ∈ ℕ$、最小境界 $b_{\text{min}} > 0$、初期値 $b_0 ≥ b_{\text{min}}$、および勾配削減係数閾値 $α ∈ [0,1)$ が与えられます。

$$
c_0=0
$$

と設定し、$ω_0 = \lVert \operatorname{grad} f(p_0) \rVert_{p_0}$ を使用します。

最初の反復では初期ステップサイズ $s_0 = \frac{1}{b_0}$ を使用します。

次に、最後の勾配 $X_{k-1} = \operatorname{grad} f(x_{k-1})$ と前の $ω_{k-1}$ を考慮して、値 $(b_k, ω_k, c_k)$ は $X_k = \operatorname{grad} f(p_k)$ を使用して次のケースで計算されます。

もし $\lVert X_k \rVert_{p_k} ≤ αω_{k-1}$ であれば、$\hat{b}_{k-1} ∈ [b_{\text{min}},b_{k-1}]$ とし、次のように設定します。

$$
(b_k, ω_k, c_k) = \begin{cases}   \bigl(\hat{b}_{k-1}, \lVert X_k \rVert_{p_k}, 0 \bigr) & \text{ if } c_{k-1}+1 = \hat{c}\\\\    \bigl( b_{k-1} + \frac{\lVert X_k \rVert_{p_k}^2}{b_{k-1}}, ω_{k-1}, c_{k-1}+1 \Bigr) & \text{ if } c_{k-1}+1<\hat{c}\end{cases}
$$

もし $\lVert X_k \rVert_{p_k} > αω_{k-1}$ であれば、次のように設定します。

$$
(b_k, ω_k, c_k) = \Bigl( b_{k-1} + \frac{\lVert X_k \rVert_{p_k}^2}{b_{k-1}}, ω_{k-1}, 0 \Bigr)
$$

そしてステップサイズ $s_k = \frac{1}{b_k}$ を返します。

$$
α=0
$$

の場合、これは `WNGRad` のリーマンバリアントです。

## キーワード引数

  * `adaptive=true`: `gradient_reduction``α``(が`true`の場合)を`0`に切り替えます。
  * `alternate_bound = (bk, hat_c) ->  min(gradient_bound == 0 ? 1.0 : gradient_bound, max(minimal_bound, bk / (3 * hat_c))`: $(bmin, bk, hat_c) -> hat_bk$ の関数として $\hat{k}_k$ を決定する方法
  * `count_threshold=4`: $\hat{c}$ のための `Integer`
  * `gradient_reduction::R=adaptive ? 0.9 : 0.0`: 勾配削減係数閾値 $α ∈ [0,1)$
  * `gradient_bound=norm(M, p, X)`: 境界 $b_k$。
  * `minimal_bound=1e-4`: 値 $b_{\text{min}}$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: マンifold $\mathcal M$ 上の点で、`gradient_bound` を定義するためのみに使用されます。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: マンifold $\mathcal M$ 上の点 $p$ での接ベクトルで、`gradient_bound` を定義するためのみに使用されます。
