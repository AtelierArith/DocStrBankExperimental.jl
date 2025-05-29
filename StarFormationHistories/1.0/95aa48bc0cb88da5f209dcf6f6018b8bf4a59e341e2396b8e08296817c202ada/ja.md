```
sample_sfh(bfgs_result::CompositeBFGSResult, 
           models::AbstractMatrix{<:Number},
           data::AbstractVector{<:Number},
           logAge::AbstractVector{<:Number},
           metallicities::AbstractVector{<:Number},
           Nsteps::Integer;
           ϵ::Real = 0.05, # HMC ステップサイズ
           reporter = DynamicHMC.ProgressMeterReport(),
           show_convergence::Bool = true,
           rng::AbstractRNG = default_rng())
sample_sfh(bfgs_result::CompositeBFGSResult, 
           models::AbstractVector{<:AbstractMatrix{<:Number}},
           data::AbstractMatrix{<:Number},
           logAge::AbstractVector{<:Number},
           metallicities::AbstractVector{<:Number},
           Nsteps::Integer;
           kws...)
```

`bfgs_result` における SFH フィッティング結果を取り込み、DynamicHMC.jl からハミルトンモンテカルロ (HMC) サンプラーを初期化して、ポスターリオールから `Nsteps` の独立したサンプルを抽出します。

主なメソッドシグネチャは、`models` と `data` のフラットな形式を使用します。詳細については、[`StarFormationHistories.composite!`](@ref) のフラットな呼び出しシグネチャに関するノートや、`models` をこのフラットな形式に再配置するのを容易にする [`stack_models`](@ref StarFormationHistories.stack_models) を参照してください。

# 引数

  * `models, data, logAge, metallicities` は [`fit_sfh`](@ref) と同様です。
  * `Nsteps` は抽出したいモンテカルロサンプルの数です。

# キーワード引数

  * `ϵ` は HMC ステップサイズです。サンプリング後に HMC サンプルの収束がチェックされ、収束警告が発行された場合は、この値を減少させるべきです。
  * `reporter` は DynamicHMC.jl の有効なレポータタイプで、`NoProgressReport`、基本的なプログレスメーター用の `ProgressMeterReport`、またはより詳細なレポート用の `LogProgressReport` のいずれかです。
  * `show_convergence` が `true` の場合、サンプルの収束統計がデフォルトの表示に送信されます。
  * `rng` はランダムサンプルを生成する際に使用される `Random.AbstractRNG` サンプラーインスタンスです。

# 戻り値

2つの要素を持つ `NamedTuple`：

  * `posterior_matrix` は `(npar, Nsteps)` の次元を持つ `Matrix` で、`npar` は問題のフィッティング変数の数であり、`npar = length(bfgs_result.mle.μ)` です。各列は1つの独立したサンプルです。
  * `tree_statistics` には、`DynamicHMC.Diagnostics.summarize_tree_statistics` で表示できる収束統計が含まれています。

# 参照

  * [`tsample_sfh`(@ref StarFormationHistories.tsample_sfh) はマルチスレッド版です。

```
