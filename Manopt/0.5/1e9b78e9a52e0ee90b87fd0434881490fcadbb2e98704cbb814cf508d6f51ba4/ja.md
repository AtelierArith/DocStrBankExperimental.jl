```
difference_of_convex_proximal_point(M, grad_h, p=rand(M); kwargs...)
difference_of_convex_proximal_point(M, mdcpo, p=rand(M); kwargs...)
difference_of_convex_proximal_point!(M, grad_h, p; kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, p; kwargs...)
```

凸の差の近接点アルゴリズム [SouzaOliveira:2015](@cite) を計算して、次を最小化します。

$$
    \operatorname*{arg\,min}_{p∈\mathcal M} g(p) - h(p)
$$

ここで、$h$ のサブ勾配 $∂h$ を提供し、次のいずれかを指定する必要があります。

  * `g` の近接写像 $\operatorname{prox}_{λg}$ を関数 `prox_g(M, λ, p)` または `prox_g(M, q, λ, p)` として
  * サブソルバーを使用して近接写像を計算するための関数 `g` と `grad_g`
  * `sub_problem=` と `sub_state=` で指定された独自のサブソルバー

このアルゴリズムは、開始点 `p`= $p^{(0)}$ が与えられたときに次のステップを実行します。その後、$k=0,1,…$ の間で繰り返します。

1. $$
    X^{(k)}  ∈ \operatorname{grad} h(p^{(k)})
    $$
2. $$
    q^{(k)} = \operatorname{retr}_{p^{(k)}}(λ_kX^{(k)})
    $$
3. $$
    r^{(k)} = \operatorname{prox}_{λ_kg}(q^{(k)})
    $$
4. $$
    X^{(k)} = \operatorname{retr}^{-1}_{p^{(k)}}(r^{(k)})
    $$
5. ステップサイズ $s_k$ を計算し
6. $$
    p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(s_kX^{(k)})
    $$

    を設定します。

`stopping_criterion` が満たされるまで。

修正されたバリアントの詳細については、[AlmeidaNetoOliveiraSouza:2020](@cite) を参照してください。ここでは、ステップ 4-6 がわずかに変更されており、ここでの古典的な近接点法は $s_k = 1$ の場合に得られ、通常の線形探索法を使用できます。

# キーワード引数

  * `λ`:                          ( `k -> 1/2` ) 近接パラメータの列を返す関数 $λ_k$
  * `cost=nothing`: デバッグ理由/分析のためにコスト `f` を提供
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目になります。
  * `gradient=nothing`: デバッグ/分析のために $\operatorname{grad} f$ を指定するか、`stopping_criterion` を強化
  * `prox_g=nothing`: サブ問題のための近接写像を指定するか、次の両方を指定
  * `g=nothing`: 関数 `g` を指定。
  * `grad_g=nothing`: `g` の勾配を指定。`g` と `grad_g` の両方が指定されている場合、サブソルバーが自動的に設定されます。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize=`[`ConstantLength`](@ref)`()`: ステップサイズを決定する [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`：停止基準が満たされていることを示すファンクタ。`gradient` が提供されている場合、[`StopWhenGradientNormLess`](@ref)`(1e-8)` が [`|`](@ref StopWhenAny) とともに追加されます。
  * `sub_cost=`[`ProximalDCCost`](@ref)`(g, copy(M, p), λ(1))`): `g` が提供されるとすぐに初期化されるデフォルトの `sub_problem` 内で使用されるコスト。これは `sub_objective=` キーワードを定義するために使用され、したがって `sub_objective` を直接設定した場合は影響しません。
  * `sub_grad=`[`ProximalDCGrad`](@ref)`(grad_g, copy(M, p), λ(1); evaluation=evaluation)`: `grad_g` が提供されるとすぐに初期化されるデフォルトの `sub_problem` 内で使用される勾配。これは `sub_objective=` キーワードを定義するために使用され、したがって `sub_objective` を直接設定した場合は影響しません。
  * `sub_hess`:              (デフォルトで `sub_grad` を使用した有限差分近似): デフォルトソルバーが必要とする `sub_cost` のヘッセ行列を指定します。
  * `sub_kwargs=``(;)`: サブソルバーの目的の [`decorate_objective!`](@ref)、サブソルバーの状態の [`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_objective`:         `sub_cost=`, `sub_grad=`, および提供されている場合は `sub_hess` に基づく勾配またはヘッセ行列の目的。これは `sub_problem=` キーワードを定義するために使用され、したがって `sub_problem` を直接設定した場合は影響しません。
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバーまたは閉じた形式の解法関数の問題を指定します。これは割り当て可能またはインプレースです。
  * `sub_state=`([`GradientDescentState`](@ref) または [`TrustRegionsState`](@ref) が `sub_hessian` が提供されている場合): 使用するサブソルバーを指定する状態。閉じた形式の解法の場合、これは関数のタイプを示します。
  * `sub_stopping_criterion=`([`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`[`StopWhenGradientNormLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ。これは`sub*state=`キーワードを定義するために使用され、したがって`sub*state` を直接設定した場合は影響しません。

他のすべてのキーワード引数は、状態デコレーターのための [`decorate_state!`](@ref) または目的デコレーターのための [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化器 $p^*$。ソルバーの全体的な最終状態を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードを参照してください。
