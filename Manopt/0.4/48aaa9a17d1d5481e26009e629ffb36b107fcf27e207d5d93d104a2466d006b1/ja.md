```
AdaptiveWNGradient <: DirectionUpdateRule
```

[GrapigliaStella:2023](@cite) によって導入された適応的勾配法を表します。

正の閾値 $\hat c \mathbb N$、最小境界 $b_{\mathrm{min}} > 0$、初期値 $b_0 ≥ b_{\mathrm{min}}$、および勾配減少係数閾値 $\alpha ∈ [0,1)$ を与えます。

$$
c_0=0
$$

を設定し、$\omega_0 = \lVert \operatorname{grad} f(p_0) \rvert_{p_0}$ を使用します。

最初の反復では初期ステップサイズ $s_0 = \frac{1}{b_0}$ を使用します。

次に、最後の勾配 $X_{k-1} = \operatorname{grad} f(x_{k-1})$ と前の $\omega_{k-1}$ を与えられた場合、値 $(b_k, \omega_k, c_k)$ は $X_k = \operatorname{grad} f(p_k)$ を使用して次のケースに従って計算されます。

もし $\lVert X_k \rVert_{p_k} \leq \alpha\omega_{k-1}$ であれば、$\hat b_{k-1} ∈ [b_\mathrm{min},b_{k-1}]$ とし、次のように設定します。

$$
(b_k, \omega_k, c_k) = \begin{cases}
\bigl(\hat b_{k-1}, \lVert X_k\rVert_{p_k}, 0 \bigr) & \text{ if } c_{k-1}+1 = \hat c\\
\Bigl(b_{k-1} + \frac{\lVert X_k\rVert_{p_k}^2}{b_{k-1}}, \omega_{k-1}, c_{k-1}+1 \Bigr) & \text{ if } c_{k-1}+1<\hat c
\end{cases}
$$

もし $\lVert X_k \rVert_{p_k} > \alpha\omega_{k-1}$ であれば、次のように設定します。

$$
(b_k, \omega_k, c_k) =
\Bigl( b_{k-1} + \frac{\lVert X_k\rVert_{p_k}^2}{b_{k-1}}, \omega_{k-1}, 0)
$$

そしてステップサイズ $s_k = \frac{1}{b_k}$ を返します。

$$
α=0
$$

の場合、これは `WNGRad` のリーマンバリアントです。

# フィールド

  * `count_threshold::Int`: （`4`）$\hat c$ のための `Integer`
  * `minimal_bound::Float64`: （`1e-4`）$b_{\mathrm{min}}$ のため
  * `alternate_bound::Function`: （`(bk, hat_c) -> min(gradient_bound, max(gradient_bound, bk/(3*hat_c)`) $\hat b_k$ を決定する方法としての関数
  * `gradient_reduction::Float64`: （`0.9`）
  * `gradient_bound` `norm(M, p0, grad_f(M,p0))` 境界 $b_k$。

および内部フィールド

  * $$
    ω_k
    $$

    のための `weight` は、これがゼロでない場合は $ω_0 =$`norm(M, p0, grad_f(M,p0))` に初期化され、そうでない場合は `1.0` です。
  * $$
    c_k
    $$

    のための `count` は、初期化されて $c_0 = 0$ です。

# コンストラクタ

```
AdaptiveWNGrad(M=DefaultManifold, grad_f=(M, p) -> zero_vector(M, rand(M)), p=rand(M); kwargs...)
```

すべてのデフォルトを持つフィールドはキーワード引数であり、追加のキーワード引数は次のとおりです。

  * `adaptive`:   （`true`）`gradient_reduction``α``を`0` に切り替えます。
  * `evaluation`: （`AllocatingEvaluation()`）初期化のみに使用される勾配が変異するか割り当てられるかを指定します。

```
