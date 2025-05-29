```
cyclic_proximal_point(M, f, proxes_f, p; kwargs...)
cyclic_proximal_point(M, mpo, p; kwargs...)
cyclic_proximal_point!(M, f, proxes_f; kwargs...)
cyclic_proximal_point!(M, mpo; kwargs...)
```

サイクリック近接点アルゴリズムを実行します。これは `p` のインプレースで行うことができます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`:        最小化するコスト関数 $f: \mathcal M→ℝ$
  * `proxes_f`: プロキシマルマップの配列（`Function`s） `(M,λ,p) -> q` または `(M, q, λ, p) -> q` で、$f$ の和項に対して（`evaluation`を参照）

ここで、`f` とプロキシマルマップ `proxes_f` は、[`ManifoldProximalMapObjective`](@ref) `mpo` として直接与えることもできます。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、修正された引数は2番目のものです。
  * `evaluation_order=:Linear`: ランダムに順序を入れ替えたシーケンス（`:FixedRandom`）、サイクルごとに入れ替えたシーケンス（`:Random`）またはデフォルトの線形のものを使用するかどうか。
  * `λ=iter -> 1/iter`:         （平方和可能だが和可能ではない）$λ_i$ のシーケンスを返す関数
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-12)`): 停止基準が満たされていることを示すファンクタ

その他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。
