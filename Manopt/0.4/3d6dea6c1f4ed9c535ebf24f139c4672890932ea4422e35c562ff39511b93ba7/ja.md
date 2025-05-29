```
LevenbergMarquardt(M, f, jacobian_f, p, num_components=-1)
```

最適化問題を次の形式で解きます

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \lVert f(p) \rVert^2,
$$

ここで、$f: \mathcal M → ℝ^d$ は連続微分可能な関数であり、リーマン多様体のLevenberg-Marquardtアルゴリズムを使用します [Peeters:1993](@cite)。実装はアルゴリズム1 [AdachiOkunoTakeda:2022](@cite) に従います。

# 入力

  * `M`:              多様体 $\mathcal M$
  * `f`:              コスト関数 $f: \mathcal M→ℝ^d$
  * `jacobian_f`:     $f$ のヤコビアン。ヤコビアンは、ヤコビアンを計算する点での接空間の基底を指定するキーワード引数 `basis_domain` を受け取る必要があります。デフォルトでは `DefaultOrthonormalBasis` であるべきです。
  * `p`:              初期値 $p ∈ \mathcal M$
  * `num_components`: コスト関数によって返されるベクトルの長さ（`d`）。デフォルトの値は -1 で、これは `f` をもう1回呼び出すことで自動的に決定されることを意味します。これは `evaluation` が `AllocatingEvaluation` の場合にのみ可能であり、ミューテーション評価の場合はこの値を明示的に指定する必要があります。

これらは [`NonlinearLeastSquaresObjective`](@ref) としても渡すことができ、その場合は以下のキーワード `jacobian_tangent_basis` は無視されます。

# オプション

  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するか（デフォルト）`gradF(M, x)` の形式か、または [`InplaceEvaluation`](@ref) の形式 `gradF!(M, X, x)` かを指定します。
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) 使用する `retraction(M,x,ξ)`。
  * `stopping_criterion`:      ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1e-12)`) 停止するタイミングを示す [`StoppingCriterion`](@ref) から継承されたファンクタ。
  * `expect_zero_residual`:    (`false`) アルゴリズムが最小値での残差（目的）の値が0であることを期待するかどうか。
  * `η`:                       新しい提案点を受け入れるために必要な十分なコスト減少閾値のスケーリングファクター。許可される範囲: `0 < η < 1`。
  * `damping_term_min`:        ダンピング項の初期（および最小）値。
  * `β`:                       現在の新しい点が拒否されたときにダンピング項が乗算されるパラメータ。
  * `initial_residual_values`: コスト関数 `f` の初期残差ベクトル。
  * `initial_jacobian_f`:      コスト関数 `f` の初期ヤコビアン。
  * `jacobian_tangent_basis`:  [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) `jacobian_f` のための接空間の基底を指定します。

他のすべてのキーワード引数は、デコレーター用の [`decorate_state!`](@ref) または [`decorate_objective!`](@ref) に渡されます。もし直接 [`ManifoldGradientObjective`](@ref) を提供した場合、これらの装飾はまだ指定できます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。

# 参考文献

```
