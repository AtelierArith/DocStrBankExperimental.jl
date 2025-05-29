```
multipathfinder(fun, ndraws; kwargs...)
```

[`pathfinder`](@ref)を複数回実行して、多変量正規混合モデルをフィットさせます。

`nruns=length(init)`の場合、`nruns`の並列実行のpathfinderは、事後の多変量正規近似$q_k = q(\phi | \mu_k, \Sigma_k)$を生成します。これらは均等な重みを持つ混合モデル$q$に結合されます。

$$
q
$$

は、ランダムサンプルを生成するためにコンポーネントインデックスで拡張されます。つまり、要素$(k, \phi)$は拡張された混合モデルから引き出されます。

$$
\tilde{q}(\phi, k | \mu, \Sigma) = K^{-1} q(\phi | \mu_k, \Sigma_k),
$$

ここで、$k$はコンポーネントインデックスであり、$K=$ `nruns`です。これらのサンプルは、置換を伴って再サンプリングされます。サンプルから$k$を除外すると、$q$からのサンプルを再現します。

`importance=true`の場合、パレート平滑化重要度再サンプリングが使用され、結果として得られるサンプルは、$q$ではなくターゲット分布$p$からのサンプルをより良く近似します。これは、重要度加重サンプルが$p$に関する期待値を近似するのに不適切な場合に警告メッセージも表示します。

# 引数

  * `fun`: ターゲット分布の対数密度を表すオブジェクト。サポートされているタイプは以下の通りです：

      * シグネチャ `f(params::AbstractVector{<:Real}) -> log_density::Real` を持つ呼び出し可能なオブジェクト。
      * [LogDensityProblemsインターフェース](@extref LogDensityProblems log-density-api)を実装するオブジェクト。
      * [`SciMLBase.OptimizationFunction`](@extref): *負*の対数密度をラップします。選択した`optimizer`に必要な機能（例：勾配またはヘッセ行列関数）を持っている必要があります。
      * [`SciMLBase.OptimizationProblem`](@extref): 上記の`OptimizationFunction`と同じ特性を持つ関数と初期点を含む最適化問題。提供される場合、`init`と`dim`は無視されます。
      * [`DynamicPPL.Model`](@extref): Turingモデル。提供される場合、`init`と`dim`は無視されます。
  * `ndraws::Int`: 戻す近似サンプルの数

# キーワード

  * `init`: 各単一路径Pathfinder実行が開始される初期点の長さ`dim`の長さ`nruns`のイテレータ。`length(init)`が実装されている必要があります。`init`が提供されていない場合、`nruns`が必要であり、`fun`が提供されている場合は`dim`も必要です。
  * `nruns::Int`: 実行するPathfinderの実行回数。`init`が提供されている場合は無視されます。
  * `ndraws_per_run::Int`: 再サンプリングの前に各コンポーネントのために取得するサンプルの数。`ndraws_per_run * nruns > ndraws`となる数にデフォルト設定されています。
  * `importance::Bool=true`: サンプルのパレート平滑化重要度再サンプリングを実行します。
  * `rng::AbstractRNG=Random.default_rng()`: 擬似乱数生成器。Julia 1.7以降のデフォルトPRNGのような並列化に優しいPRNGを使用することをお勧めします。
  * `executor::Transducers.Executor`: 単一路径実行を並列で実行するかどうかを決定するTransducers.jlエグゼキュータ。デフォルトは[`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`)です。マルチスレッド計算用のトランスデューサが選択された場合、`rng`と対数密度関数がスレッドセーフであることを最初に確認する必要があります。
  * `executor_per_run::Transducers.Executor`: 各実行内でPRNG呼び出しを並列化するために使用されるTransducers.jlエグゼキュータ。デフォルトは[`Transducers.SequentialEx()`](@extref `Transducers.SequentialEx`)です。詳細については[`pathfinder`](@ref)を参照してください。
  * `kwargs...` : 残りのキーワードは[`pathfinder`](@ref)に転送されます。

# 戻り値

  * [`MultiPathfinderResult`](@ref)

```
