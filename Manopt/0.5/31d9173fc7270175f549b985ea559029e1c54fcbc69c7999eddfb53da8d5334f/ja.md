```
difference_of_convex_algorithm(M, f, g, ∂h, p=rand(M); kwargs...)
difference_of_convex_algorithm(M, mdco, p; kwargs...)
difference_of_convex_algorithm!(M, f, g, ∂h, p; kwargs...)
difference_of_convex_algorithm!(M, mdco, p; kwargs...)
```

凸の差分アルゴリズム [BergmannFerreiraSantosSouza:2024](@cite) を計算して最小化します

$$
    \operatorname*{arg\,min}_{p∈\mathcal M}\ g(p) - h(p)
$$

ここで、$f(p) = g(p) - h(p)$、$g$ および $h$ のサブ微分 $∂h$ を提供する必要があります。

このアルゴリズムは、開始点 `p`= $p^{(0)}$ が与えられたときに次のステップを実行します。その後、$k=0,1,…$ の間繰り返します。

1. $$
    X^{(k)}  ∈ ∂h(p^{(k)})
    $$

    を取ります
2. 次の反復をサブ問題の解に設定します

$$
  p^{(k+1)} ∈ \operatorname*{arg\,min}_{q ∈ \mathcal M} g(q) - ⟨X^{(k)}, \log_{p^{(k)}}q⟩
$$

停止基準が満たされるまで（`stopping_criterion` キーワードを参照）。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `gradient=nothing`:        $\operatorname{grad} f$ を指定します。デバッグ/分析または `stopping_criterion=` の強化のため。
  * `grad_g=nothing`:          `g` の勾配を指定します。指定された場合、サブソルバーが自動的に設定されます。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ。
  * `g=nothing`:               関数 `g` を指定します。指定された場合、サブソルバーが自動的に設定されます。
  * `sub_cost=`[`LinearizedDCCost`](@ref)`(g, p, initial_vector)`: デフォルトの `sub_problem` 内で使用されるコスト。これは `sub_objective=` キーワードを定義するために使用され、`sub_objective` を直接設定した場合には効果がありません。
  * `sub_grad=`[`LinearizedDCGrad`](@ref)`(grad_g, p, initial_vector; evaluation=evaluation)`: デフォルトの `sub_problem` 内で使用される勾配。これは `sub_objective=` キーワードを定義するために使用され、`sub_objective` を直接設定した場合には効果がありません。
  * `sub_hess`:              （デフォルトでは `sub_grad` を使用した有限差分近似）： `sub_cost` のヘッセ行列を指定します。これは `sub_objective=` キーワードを定義するために使用され、`sub_objective` を直接設定した場合には効果がありません。
  * `sub_kwargs=``(;)`: [`decorate_objective!`](@ref) のサブソルバーの目的、[`decorate_state!`](@ref) のサブソルバーの状態、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_objective`:         `sub_cost=`, `sub_grad=`, および提供された場合の `sub_hess` に基づく勾配またはヘッセ行列の目的。これは `sub_problem=` キーワードを定義するために使用され、`sub_problem` を直接設定した場合には効果がありません。
  * `sub_state=`([`GradientDescentState`](@ref) または [`TrustRegionsState`](@ref) もし `sub_hessian` が提供されている場合）： 使用するサブソルバーを指定する状態。閉じた形式の解のため、これは関数のタイプを示します。
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバーまたは閉じた形式の解関数の問題を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-9)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-9)`: デフォルトの `sub_state=` 内で使用される停止基準。これは `sub_state=` キーワードを定義するために使用され、`sub_state` を直接設定した場合には効果がありません。
  * `sub_stepsize=`[`ArmijoLinesearch`](@ref)`(M)`) `sub_state` 内で使用されるステップサイズを指定します。これは `sub_state=` キーワードを定義するために使用され、`sub_state` を直接設定した場合には効果がありません。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトルを指定します。

他のすべてのキーワード引数は、状態デコレーターのための [`decorate_state!`](@ref) または目的デコレーターのための [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化器 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワード。
