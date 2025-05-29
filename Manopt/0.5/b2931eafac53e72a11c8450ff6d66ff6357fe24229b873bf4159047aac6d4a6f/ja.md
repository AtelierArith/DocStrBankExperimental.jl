```
alternating_gradient_descent(M::ProductManifold, f, grad_f, p=rand(M))
alternating_gradient_descent(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
alternating_gradient_descent!(M::ProductManifold, f, grad_f, p)
alternating_gradient_descent!(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

交互勾配降下法を実行します。これは開始点 `p` のインプレースで行うことができます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ は `(M, p) -> v` として実装されています
  * `grad_f`: 勾配で、2つのケースのいずれかです

      * `ArrayPartition` を返す単一の関数であるか、[`RecursiveArrayTools.jl`](https://docs.sciml.ai/RecursiveArrayTools/stable/array_types/) からのものであるか
      * 全体の勾配の各成分部分を返すベクトル関数であるか
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、修正された引数は2番目のものです。
  * `evaluation_order=:Linear`: ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Random`）、またはデフォルトの `:Linear` を使用するかどうか。
  * `inner_iterations=5`: 次のコンポーネントに交互に移る前に、コンポーネント内で取る勾配ステップの数
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`): 停止基準が満たされていることを示すファンクタ
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `order=[1:n]`:         初期の順序、ここで `n` は `gradF` の勾配の数です。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、再収束に関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

# 出力

通常、得られた（近似的な）最小化器、詳細については [`get_solver_return`](@ref) を参照してください。

!!! 注     各（コンポーネント）勾配の入力は依然として全体のベクトル `X` であり、他のすべての `i` 番目の入力コンポーネントは固定されていると仮定され、`i` 番目のコンポーネントの勾配が計算され / 返されます。 ```
