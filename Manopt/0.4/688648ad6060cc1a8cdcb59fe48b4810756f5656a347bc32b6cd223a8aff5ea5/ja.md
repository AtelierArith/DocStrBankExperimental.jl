```
cyclic_proximal_point(M, f, proxes_f, p)
cyclic_proximal_point(M, mpo, p)
```

サイクリック近接点アルゴリズムを実行します。

# 入力

  * `M`:        多様体 $\mathcal M$
  * `f`:        最小化するコスト関数 $f:\mathcal M→ℝ$
  * `proxes_f`: 近接写像の配列（`Function`） `(M,λ,p) -> q` または `(M, q, λ, p) -> q` で、$f$ の和項に対して（`evaluation`を参照）
  * `p`:        初期値 $p ∈ \mathcal M$

ここで `f` と近接写像 `proxes_f` は、[`ManifoldProximalMapObjective`](@ref) `mpo` として直接与えることもできます。

# オプション

  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) 近接写像が割り当てによって動作するかどうかを指定します（デフォルト）形式 `prox(M, λ, x)` または [`InplaceEvaluation`](@ref) 形式 `prox!(M, y, λ, x)`。
  * `evaluation_order`:   (`:Linear`) ランダムに順序を入れ替えたシーケンスを使用するかどうか（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Random`）またはデフォルトの線形のもの。
  * `λ`:                  (`iter -> 1/iter` ) （平方和可能だが和可能ではない）$λ_i$ のシーケンスを返す関数
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(5000) |`[`StopWhenChangeLess`](@ref)`(1e-12)`) [`StoppingCriterion`](@ref)。

他のすべてのキーワード引数は、デコレーター用の [`decorate_state!`](@ref) または目的関数用の [`decorate_objective!`](@ref) に渡されます。直接 [`ManifoldProximalMapObjective`](@ref) を提供した場合でも、これらの装飾を指定することができます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。
