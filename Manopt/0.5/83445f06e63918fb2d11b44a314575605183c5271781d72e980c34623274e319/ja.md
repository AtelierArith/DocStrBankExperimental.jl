```
proximal_point(M, prox_f, p=rand(M); kwargs...)
proximal_point(M, mpmo, p=rand(M); kwargs...)
proximal_point!(M, prox_f, p; kwargs...)
proximal_point!(M, mpmo, p; kwargs...)
```

[FerreiraOliveira:2002](@cite) による近接点アルゴリズムを実行します。これは次のように読みます。

$$
p^{(k+1)} = \operatorname{prox}_{λ_kf}(p^{(k)})
$$

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `prox_f`: 近接写像 `(M,λ,p) -> q` または `(M, q, λ, p) -> q` で、$f$ の和項のためのものです（`evaluation` を参照）

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、修正された引数は2番目のものです。
  * `f=nothing`: 最小化するコスト関数 $f: \mathcal M→ℝ$。アルゴリズムを実行するためには $f$ は必要ありませんが、コストを記録したり、コスト関数を必要とする停止基準を使用する場合には必要です。
  * `λ= k -> 1.0`: （平方和可能だが和可能ではない）$λ_i$ の列を返す関数
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-12)`): 停止基準が満たされていることを示すファンクタ

その他のすべてのキーワード引数は、状態デコレーターのために [`decorate_state!`](@ref) に、目的デコレーターのために [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。
