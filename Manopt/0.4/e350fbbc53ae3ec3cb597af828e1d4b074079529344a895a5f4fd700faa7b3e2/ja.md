```
difference_of_convex_algorithm(M, f, g, ∂h, p=rand(M); kwargs...)
difference_of_convex_algorithm(M, mdco, p; kwargs...)
```

凸の差分アルゴリズム [BergmannFerreiraSantosSouza:2023](@cite) を計算して最小化します

$$
    \operatorname*{arg\,min}_{p∈\mathcal M}\  g(p) - h(p)
$$

ここで、$f(p) = g(p) - h(p)$、$g$ および $h$ のサブ微分 $∂h$ を提供する必要があります。

このアルゴリズムは、開始点 `p`= $p^{(0)}$ が与えられたときに次のステップを実行します。その後、$k=0,1,\ldots$ の間繰り返します。

1. $$
    X^{(k)}  ∈ ∂h(p^{(k)})
    $$

    を取ります
2. 次の反復をサブ問題の解に設定します

$$
  p^{(k+1)} ∈ \operatorname*{argmin}_{q ∈ \mathcal M} g(q) - ⟨X^{(k)}, \log_{p^{(k)}}q⟩
$$

`stopping_criterion` が満たされるまで。

# オプションのパラメータ

  * `evaluation`          ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するかどうかを指定します（デフォルト）`grad_f(M, p)` 形式または [`InplaceEvaluation`](@ref) 形式 `grad_f!(M, X, x)`
  * `gradient`            (`nothing`) $\operatorname{grad} f$ を指定します。デバッグ / 分析または `stopping_criterion=` の強化用
  * `grad_g`              (`nothing`) `g` の勾配を指定します。指定された場合、サブソルバーが自動的に設定されます。
  * `initial_vector`      (`zero_vector(M, p)`) サブグラデーション結果を格納するための内部接線ベクトルを初期化します。
  * `stopping_criterion`  ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenChangeLess`](@ref)`(1e-8)`) アルゴリズムのための [`StoppingCriterion`](@ref) です。これは、`gradient` が提供されている場合に、[`StopWhenGradientNormLess`](@ref)`(1e-8)` を含みます。

[`ManifoldDifferenceOfConvexObjective`](@ref) `mdco` を指定した場合、さらに

  * `g`                   - (`nothing`) 関数 `g` を指定します。指定された場合、サブソルバーが自動的に設定されます。

サブソルバーのためのパラメータはいくつかありますが、最も簡単なのは `grad_g=` を提供することです。これにより、必須の関数 `g` とともにデフォルトのコストと勾配が生成され、デフォルトのサブソルバーに渡されます。したがって、最も簡単な呼び出し例は次のようになります。

```
difference_of_convex_algorithm(M, f, g, grad_h, p; grad_g=grad_g)
```

# サブ問題のオプションのパラメータ

  * `sub_cost`              ([`LinearizedDCCost`](@ref)`(g, p, initial_vector)`) デフォルトの `sub_problem` 内で使用されるコスト。これが以前の `g` を使用して構築されたデフォルトよりも効率的なバージョンがある場合は、これを使用します。
  * `sub_grad`              ([`LinearizedDCGrad`](@ref)`(grad_g, p, initial_vector; evaluation=evaluation)` デフォルトの `sub_problem` 内で使用される勾配。`grad_g` が提供されている場合はデフォルトで生成されます。キーワードを上書きすることで独自のものを指定できます。
  * `sub_hess`              (デフォルトでは有限差分近似) サブ問題のヘッセ行列を指定します。デフォルトのソルバーは、`sub_state` が必要です。
  * `sub_kwargs`            (`(;)`) `sub_state` にキーワード引数を渡します。形式は `Dict(:kwname=>value)` ですが、`sub_state` を直接設定する場合は除きます。
  * `sub_objective`         (最後の3つのキーワードに基づく勾配またはヘッセ行列の目的) `sub_problem` 内で使用される目的を提供します（ユーザーによって指定されていない場合）。
  * `sub_problem`           ([`DefaultManoptProblem`](@ref)`(M, sub_objective)` サブソルバーが実行されるための manopt 問題を指定します。閉じた形式の解のための関数を提供することもできます。その場合、`evaluation=` はこの関数の形式に考慮されます。
  * `sub_state`             ([`TrustRegionsState`](@ref) デフォルトでは、`sub_hessian` を提供する必要があります; `sub_kwargs` で装飾されます)。`sub_problem` を解くためにソルバーを選択します。`sub_problem` が関数（閉じた形式の解）の場合、これは `evaluation` に設定され、閉じた形式の解の評価タイプに応じて変更できます。
  * `sub_stopping_criterion` ([`StopAfterIteration`](@ref)`(300) |`[`StopWhenStepsizeLess`](@ref)`(1e-9) |`[`StopWhenGradientNormLess`](@ref)`(1e-9)`) デフォルトの `sub_state=` 内で使用される停止基準
  * `sub_stepsize`           ([`ArmijoLinesearch`](@ref)`(M)`) `sub_state` 内で使用されるステップサイズを指定します。

他のすべては、内部の [`DifferenceOfConvexState`](@ref) を装飾するために渡されます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。 ```
