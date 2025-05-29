```
Frank_Wolfe_method(M, f, grad_f, p=rand(M))
Frank_Wolfe_method(M, gradient_objective, p=rand(M); kwargs...)
Frank_Wolfe_method!(M, f, grad_f, p; kwargs...)
Frank_Wolfe_method!(M, gradient_objective, p; kwargs...)
```

フランク・ウォルフアルゴリズムを実行して、制約付き問題に対して$\mathcal C ⊂ \mathcal M$のために計算します。

$$
    \operatorname*{arg\,min}_{p∈\mathcal C} f(p),
$$

ここで、主なステップはアルゴリズム内の制約最適化であり、すなわちサブ問題（オラクル）

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

すべての反復$ p*k $に対して、ステップサイズ$s*k≤1:とともに。アルゴリズムは`p`のインプレースで実行できます。

このアルゴリズムは、[WeberSra:2022](@cite)に触発されていますが、少し一般的です。

次の反復は、$p_{k+1} = γ_{p_k,q_k}(s_k)$によって与えられ、デフォルトでは$γ$は2点間の最短測地線ですが、リトラクションとその逆を使用するように変更することもできます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体$\mathcal M$
  * `f`: コスト関数$f: \mathcal M→ ℝ$を`(M, p) -> v`として実装
  * `grad_f`: 関数$f$の（リーマン）勾配$\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$を`(M, p) -> X`または`(M, X, p) -> X`として、`X`をインプレースで計算する関数
  * `p`: 多様体$\mathcal M$上の点

`f`および`grad_f`の代わりに、対応する[`AbstractManifoldGradientObjective`](@ref) `gradient_objective`を直接提供できます。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目になります。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション$\operatorname{retr}$、[リトラクションに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize=`[`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)`: ステップサイズを決定する[`Stepsize`](@ref)から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`): 停止基準が満たされていることを示すファンクタ
  * `sub_cost=`[`FrankWolfeCost`](@ref)`(p, X)`: フランク・ウォルフサブ問題のコスト。これは`sub_objective=`キーワードを定義するために使用され、`sub_objective`を直接設定した場合は効果がありません。
  * `sub_grad=`[`FrankWolfeGradient`](@ref)`(p, X)`: フランク・ウォルフサブ問題の勾配。これは`sub_objective=`キーワードを定義するために使用され、`sub_objective`を直接設定した場合は効果がありません。
  * `sub_kwargs=``(;)`: サブソルバーの目的の[`decorate_objective!`](@ref)、サブソルバーの状態の[`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_objective=`[`ManifoldGradientObjective`](@ref)`(sub_cost, sub_gradient)`: フランク・ウォルフサブ問題の目的。これは`sub_problem=`キーワードを定義するために使用され、`sub_problem`を直接設定した場合は効果がありません。
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバー用の問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state=`[`GradientDescentState`](@ref)`(M, copy(M,p))`: 使用するサブソルバーを指定する状態。閉じた形式の解の場合、これは関数のタイプを示します。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 現在の反復での勾配を格納する多様体$\mathcal M$上の点$p$での接ベクトル
  * `sub_stopping_criterion=``[`StopAfterIteration`](@ref)`(300)`[` | `](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ。これは`sub*state=`キーワードを定義するために使用され、`sub*state`を直接設定した場合は効果がありません。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 現在の反復での勾配を格納する多様体$\mathcal M$上の点$p$での接ベクトル

他のすべてのキーワード引数は、状態デコレーターの[`decorate_state!`](@ref)または目的デコレーターの[`decorate_objective!`](@ref)に渡されます。

[`ManifoldGradientObjective`](@ref)を直接提供する場合、`evaluation=`キーワードは無視されます。デコレーションは目的に対して適用されます。

# 出力

得られた（近似的な）最小化点$p^*$、詳細については[`get_solver_return`](@ref)を参照してください。 ```
