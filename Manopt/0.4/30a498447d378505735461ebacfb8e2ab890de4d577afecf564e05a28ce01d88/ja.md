```
Frank_Wolfe_method(M, f, grad_f, p)
Frank_Wolfe_method(M, gradient_objective, p; kwargs...)
```

フランク・ウォルフアルゴリズムを実行して、$\mathcal C \subset \mathcal M$ に対して

$$
    \operatorname*{arg\,min}_{p∈\mathcal C} f(p),
$$

を計算します。ここで、主なステップはアルゴリズム内の制約付き最適化であり、すなわちサブ問題（オラクル）は

$$
    q_k = \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

すべての反復 $p_k$ に対して、ステップサイズ $s_k≤1$ を使用します。デフォルトでは $s_k = \frac{2}{k+2}$ です。このアルゴリズムは [WeberSra:2022](@cite) に触発されていますが、少し一般的です。

次の反復は $p_{k+1} = γ_{p_k,q_k}(s_k)$ で与えられ、デフォルトでは $γ$ は2点間の最短測地線ですが、リトラクションとその逆を使用するように変更することもできます。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化子 $p^*$ を見つけるためのコスト関数 $f: \mathcal M→ℝ$
  * `grad_f`: f の勾配 $\operatorname{grad}f: \mathcal M → T\mathcal M$
  * `p`:      初期値 $p ∈ \mathcal C$、これは実際に実行可能な点である必要があります

`f` と `grad_f` の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective` を直接提供することもできます。

# キーワード引数

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) `grad_f` がインプレースまたはアロケーション（デフォルト）関数であるかどうか
  * `initial_vector`:     (`zero_vectoir(M,p)`) 内部勾配接ベクトルを初期化する方法
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(500) |`[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`) 停止基準
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) リトラクションの種類
  * `stepsize`:           ([`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)` 使用する [`Stepsize`](@ref); 常に1未満である必要があります。デフォルトはフランクとウォルフによって提案されたものです: $s_k = \frac{2}{k+2}$。
  * `sub_cost`:           ([`FrankWolfeCost`](@ref)`(p, initiel_vector)`) フランク・ウォルフサブ問題のコストで、デフォルトでは現在の反復と（サブ）勾配を使用してデフォルトコストを定義します。これによりデフォルトの `sub_objective` が定義されます。これを設定した場合、または `sub_problem` を直接設定した場合は無視されます。
  * `sub_grad`:           ([`FrankWolfeGradient`](@ref)`(p, initial_vector)`) フランク・ウォルフサブ問題の勾配で、デフォルトでは現在の反復と（サブ）勾配を使用してデフォルト勾配を定義します。これによりデフォルトの `sub_objective` が定義されます。これを設定した場合、または `sub_problem` を直接設定した場合は無視されます。
  * `sub_objective`:      ([`ManifoldGradientObjective`](@ref)`(sub_cost, sub_gradient)`) フランク・ウォルフサブ問題の目的で、これによりデフォルトの `sub_problem` が定義されます。これを手動で `sub_problem` を設定した場合は無視されます。
  * `sub_problem`:        ([`DefaultManoptProblem`](@ref)`(M, sub_objective)`) 解決すべきフランク・ウォルフサブ問題。これは3つの形式で与えることができます。

    1. [`AbstractManoptProblem`](@ref) として、`sub_state` が使用するソルバーを指定します。
    2. 閉じた形式の解として、現在の反復 `p` と（サブ）勾配 `X` を与えられたときにサブ問題を解決する関数 `(M, p, X) -> q`。
    3. 閉じた形式の解として、`q` の代わりに機能する関数 `(M, q, p, X) -> q`。

    ポイント2および3の場合、`sub_state` は対応する [`AbstractEvaluationType`](@ref)、[`AllocatingEvaluation`](@ref) および [`InplaceEvaluation`](@ref) に設定する必要があります。
  * `sub_state`:          (`evaluation` が `sub_problem` が関数の場合、デコレートされた [`GradientDescentState`](@ref) それ以外の場合) 関数の場合、評価はフランク・ウォルフの `evaluation` キーワードから継承されます。
  * `sub_kwargs`:         (`(;)`) `sub_problem` が関数でない場合、`sub_state` のデフォルト状態をデコレートするためのキーワード引数

他のすべてのキーワード引数は、デコレーター用に [`decorate_state!`](@ref) に、または [`decorate_objective!`](@ref) に渡されます。`ManifoldGradientObjective` を直接提供する場合でも、これらの装飾は指定できます。

# 出力

得られた（近似的な）最小化子 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。 ```
