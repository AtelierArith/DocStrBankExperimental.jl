```
pathfinder(fun; kwargs...)
```

対数密度を最大化する際に遭遇した最良の多変量正規近似を見つけます。

最適化の軌跡から、Pathfinderは対数密度関数によって指定された分布への一連の（多変量正規）近似を構築します。証拠下限（ELBO）を最大化する近似、または同等に、近似と真の分布との間のKLダイバージェンスを最小化する近似が返されます。

多変量正規分布の共分散は、最大で前の `history_length` ステップを使用して構築された逆ヘッセ行列の近似です。

# 引数

  * `fun`: 対象分布の対数密度を表すオブジェクト。サポートされているタイプは以下を含みます：

      * シグネチャ `f(params::AbstractVector{<:Real}) -> log_density::Real` を持つ呼び出し可能なオブジェクト。
      * [LogDensityProblems インターフェース](@extref LogDensityProblems log-density-api) を実装するオブジェクト。
      * [`SciMLBase.OptimizationFunction`](@extref): *負*の対数密度をラップします。選択した `optimizer` に必要な機能（例：勾配またはヘッセ行列関数）を持っている必要があります。
      * [`SciMLBase.OptimizationProblem`](@extref): 上記の `OptimizationFunction` と同じ特性を持つ関数と初期点を含む最適化問題。提供された場合、`init` と `dim` は無視されます。
      * [`DynamicPPL.Model`](@extref): Turing モデル。提供された場合、`init` と `dim` は無視されます。

# キーワード

  * `dim::Int`: 対象分布の次元。`init` が提供された場合は無視されます。
  * `init::AbstractVector{<:Real}`: 最適化を開始するための長さ `dim` の初期点。提供されない場合、`fun` に初期点が含まれていない場合は、`Vector{Float64}` 型の長さ `dim` の初期点が作成され、`init_sampler` を使用して埋められます。
  * `init_scale::Real`: デフォルトの `init_sampler` が範囲 $[-s, s]$ で均等にエントリをサンプリングするためのスケールファクター $s$。
  * `init_sampler`: `(rng, x) -> x` のシグネチャを持つ関数で、初期点を生成するために長さ `dims` のベクトルをインプレースで修正します。
  * `ndraws_elbo::Int=5`: ELBOを推定するために使用されるサンプルの数。
  * `ndraws::Int=ndraws_elbo`: 返される近似サンプルの数。
  * `rng::Random.AbstractRNG`: サンプルを引くために使用される乱数生成器。
  * `executor::Transducers.Executor`: ELBO計算を並列で実行するかどうかを決定する Transducers.jl のエグゼキュータ。デフォルトは、並列化を行わない [`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`) です。`rng` がスレッドセーフであり、対数密度関数が内部状態を持たないことが知られている場合、[`Transducers.PreferParallel()`](@extref `Transducers.PreferParallel`) を使用して対数密度評価を並列化できます。これは一般的に高価な対数密度関数に対してのみ高速です。
  * `history_length::Int=6`: 逆ヘッセ行列を近似するために使用される履歴のサイズ。
  * `optimizer`: 軌跡を構築するために使用される最適化手法。コールバックをサポートしている限り、[Optimization.jl](https://docs.sciml.ai/Optimization/stable/) と互換性のある任意の最適化手法を使用できます。デフォルトは [`Optim.LBFGS`](@extref Optim `algo/lbfgs`)`(; m=history_length, linesearch=LineSearches.HagerZhang(), alphaguess=LineSearches.InitialHagerZhang())` です。
  * `adtype::`[`ADTypes.AbstractADType`](@extref): `fun` がすでに勾配を指定していない場合に、勾配を計算するために使用される自動微分バックエンドを指定します。デフォルトは [`ADTypes.AutoForwardDiff()`](@extref `ADTypes.AutoForwardDiff`) です。 [Optimization.jlの自動微分推奨](@extref Optimization ad) を参照してください。
  * `ntries::Int=1_000`: 最適化を試みる回数。失敗した場合は再起動します。再起動の前に、`init_sampler` を使用して新しい初期点が引かれます。
  * `fail_on_nonfinite::Bool=true`: `true` の場合、対数密度が `NaN` または `Inf` であるか、勾配が非有限である場合、最適化は失敗します。`nretries > 0` の場合、再初期化後に最適化が再試行されます。
  * `kwargs...` : 残りのキーワードは [`Optimization.solve`](@extref Optimization `CommonSolve.solve`) に転送されます。

# 戻り値

  * [`PathfinderResult`](@ref)

```
