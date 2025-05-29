```
alternating_gradient_descent(M::ProductManifold, f, grad_f, p=rand(M))
alternating_gradient_descent(M::ProductManifold, ago::ManifoldAlternatingGradientObjective, p)
```

交互勾配降下法を実行します

# 入力

  * `M`:      積多様体 $\mathcal M = \mathcal M_1 × \mathcal M_2 × ⋯ ×\mathcal M_n$
  * `f`:      `M` 上で定義された目的関数（コスト）。
  * `grad_f`: 勾配で、2つのケースのいずれかであることができます

      * 単一の関数が `ArrayPartition` を返すか
      * 各コンポーネント部分の全体の勾配を返すベクトル関数であるか
  * `p`:      初期値 $p_0 ∈ \mathcal M$

# オプション

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するか（デフォルト）形式 `gradF(M, x)` または [`InplaceEvaluation`](@ref) 形式 `gradF!(M, X, x)`（要素ごと）を指定します。
  * `evaluation_order`:   (`:Linear`) ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Random`）またはデフォルトの `:Linear` を使用するかどうか。
  * `inner_iterations`:   (`5`) 次のコンポーネントに交互に移る前に、コンポーネント内で取る勾配ステップの数
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(1000)`) [`StoppingCriterion`](@ref)
  * `stepsize`:           ([`ArmijoLinesearch`](@ref)`()`) [`Stepsize`](@ref)
  * `order`:              (`[1:n]`) 初期の順序、ここで `n` は `gradF` の勾配の数です。
  * `retraction_method`:  (`default_retraction_method(M, typeof(p))`) 使用する `retraction(M, p, X)`。

# 出力

通常、得られた（近似的な）最小化器、詳細については [`get_solver_return`](@ref) を参照してください。

!!! 注     各（コンポーネント）勾配の入力は依然として全体のベクトル `X` であり、他のすべての `i` 番目の入力コンポーネントは固定されていると仮定され、`i` 番目のコンポーネントの勾配が計算され / 返されます。
