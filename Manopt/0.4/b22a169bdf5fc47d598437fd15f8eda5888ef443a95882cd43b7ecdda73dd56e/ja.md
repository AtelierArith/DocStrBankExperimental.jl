```
difference_of_convex_proximal_point(M, grad_h, p=rand(M); kwargs...)
difference_of_convex_proximal_point(M, mdcpo, p=rand(M); kwargs...)
```

凸の差の近接点アルゴリズム [SouzaOliveira:2015](@cite) を計算して

$$
    \operatorname*{arg\,min}_{p∈\mathcal M} g(p) - h(p)
$$

を最小化します。

ここで、$h$ の (部分) 勾配 $∂h$ を提供し、次のいずれかを指定する必要があります。

  * `g` の近接写像 $\operatorname{prox}_{\lambda g}$ を関数 `prox_g(M, λ, p)` または `prox_g(M, q, λ, p)` として
  * 近接写像をサブソルバーを使用して計算するための関数 `g` と `grad_g`
  * あなた自身のサブソルバー、以下のオプションのキーワードを参照

このアルゴリズムは、開始点 `p`= $p^{(0)}$ が与えられたときに次のステップを実行します。その後、$k=0,1,\ldots$ の間繰り返します。

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

`stopping_criterion` が満たされるまで。ステップ 4-6 がわずかに変更されている修正バリアントの詳細については、[AlmeidaNetoOliveiraSouza:2020](@cite) を参照してください。ここでは、$s_k = 1$ の場合に DC 関数の古典的な近接点法が得られ、通常の線形探索法を使用できます。

# オプションのパラメータ

  * `λ`:                          ( `i -> 1/2` ) 近接パラメータ λi のシーケンスを返す関数
  * `evaluation`:                 ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するかどうかを指定します（デフォルト）形式 `gradF(M, x)` または [`InplaceEvaluation`](@ref) 形式 `gradF!(M, X, x)` のいずれか。
  * `cost`:                       (`nothing`) デバッグ理由/分析のためにコスト `f` を提供します。これを使用して、以前の `g` よりも効率的なバージョンがある場合。
  * `gradient`:                   (`nothing`) デバッグ/分析のために $\operatorname{grad} f$ を指定するか、`stopping_criterion` を強化します。
  * `prox_g`:                     (`nothing`) サブ問題のための近接写像を指定するか、次の両方を指定します。
  * `g`:                          (`nothing`) 関数 `g` を指定します。
  * `grad_g`:                     (`nothing`) `g` の勾配を指定します。`g` と `grad_g` の両方が指定されている場合、サブソルバーが自動的に設定されます。
  * `inverse_retraction_method`:  (`default_inverse_retraction_method(M)`) 使用する逆引き戻し法（ステップ 4 を参照）。
  * `retraction_method`:          (`default_retraction_method(M)`) 使用する引き戻し（ステップ 2 を参照）
  * `stepsize`:                   ([`ConstantStepsize`](@ref)`(M)`) 修正アルゴリズムを実行するための [`Stepsize`](@ref) を指定します（実験的）ファンクタ。
  * `stopping_criterion`:         ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenChangeLess`](@ref)`(1e-8)`) アルゴリズムのための [`StoppingCriterion`](@ref)、`gradient` が提供されている場合は [`StopWhenGradientNormLess`](@ref)`(1e-8)` も含まれます。

サブソルバーのためのパラメータは複数ありますが、最も簡単なのは関数 `g` と `grad_g` を提供することです。これにより、必須の関数 `g` とともにデフォルトのコストと勾配が生成され、デフォルトのサブソルバーに渡されます。したがって、最も簡単な例の呼び出しは次のようになります。

```
difference_of_convex_proximal_point(M, grad_h, p0; g=g, grad_g=grad_g)
```

# サブ問題のためのオプションのパラメータ

  * `sub_cost`:               ([`ProximalDCCost`](@ref)`(g, copy(M, p), λ(1))`) デフォルトの `sub_problem` 内で使用されるコスト。`g` が提供されるとすぐに初期化されます。
  * `sub_grad`:               ([`ProximalDCGrad`](@ref)`(grad_g, copy(M, p), λ(1); evaluation=evaluation)`）デフォルトの `sub_problem` 内で使用される勾配。`grad_g` が提供されるとすぐに初期化されます。これを上書きして独自のものを指定できます。
  * `sub_hess`:               （デフォルトでは有限差分近似）サブ問題のヘッセ行列を指定します。デフォルトのソルバーは `sub_state` が必要です。
  * `sub_kwargs`:             (`(;)`) `sub_state` にキーワード引数を渡します。形式は `Dict(:kwname=>value)` ですが、`sub_state` を直接設定する場合は除きます。
  * `sub_objective`:          （最後の 3 つのキーワードに基づく勾配またはヘッセ行列の目的）`sub_problem` 内で使用される目的を提供します（ユーザーによって指定されていない場合）。
  * `sub_problem`:            ([`DefaultManoptProblem`](@ref)`(M, sub_objective)`）サブソルバーが実行するための manopt 問題を指定します。閉じた形式の解法のための関数を提供することもできます。この場合、`evaluation=` はこの関数の形式に考慮されます。
  * `sub_state`:              ([`TrustRegionsState`](@ref)) `sub_Hessian` を提供する必要があります。`sub*kwargs` で装飾されます。`sub*problem` を解決するためにソルバーを指定します。
  * `sub_stopping_criterion`: ([`StopAfterIteration`](@ref)`(300) |`[`StopWhenStepsizeLess`](@ref)`(1e-9) |`[`StopWhenGradientNormLess`](@ref)`(1e-9)`) デフォルトの `sub_state` 内で使用される停止基準。

他のすべては、内部の [`DifferenceOfConvexProximalState`](@ref) を装飾するために渡されます。

# 出力

得られた (近似) 最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。 ```
