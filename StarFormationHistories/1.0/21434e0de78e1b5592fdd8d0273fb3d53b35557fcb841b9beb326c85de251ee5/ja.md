```
hmc_sample(models::AbstractVector{T},
           data::AbstractMatrix{<:Number},
           nsteps::Integer [, nchains::Integer];
           rng::Random.AbstractRNG=Random.default_rng(),
           kws...)
           where {S <: Number, T <: AbstractMatrix{S}}
hmc_sample(models::AbstractMatrix{S},
           data::AbstractVector{<:Number},
           nsteps::Integer;
           rng::AbstractRNG=default_rng(),
           kws...)
           where S <: Number

係数 `coeffs` の事後分布をサンプリングする関数で、観測データ `data` の完全モデルは `sum(models .* coeffs)` です。Dolphin 2002 の式 7–10 で定義されたポアソン尤度比と、係数の対数変換を使用して、フィッティング変数がすべての実数にわたって連続かつ微分可能になるようにします。サンプリングは、[DynamicHMC.jl](https://github.com/tpapp/DynamicHMC.jl) に実装された No-U-Turn サンプラーを使用して行われ、これは動的ハミルトンモンテカルロの一形態です。

2 番目の呼び出しシグネチャは、`models` と `data` のフラットな形式をサポートしています。詳細については、[`StarFormationHistories.composite!`](@ref) のフラットな呼び出しシグネチャに関するノートを参照してください。

# 引数

  * `models::AbstractVector{<:AbstractMatrix{<:Number}}` は、観測されたヘス図を構成する単純な星団のテンプレートヘス図を表す同サイズの行列のベクトルです。
  * `data::AbstractMatrix{<:Number}` は、観測データのヘス図です。
  * `nsteps::Integer` は、チェーンごとに引き出すサンプルの数です。

# オプション引数

  * `nchains::Integer`: この引数が提供されない場合、このメソッドは単一のチェーンを返します。この引数が提供されると、利用可能なすべての Julia スレッドを使用して `nchains` チェーンをサンプリングし、個々のチェーンのベクトルを返します。

# キーワード引数

  * `rng::Random.AbstractRNG` は、DynamicHMC.jl に渡される乱数生成器です。`nchains` が提供される場合、このメソッドは並列でサンプリングを試み、`Random.default_rng()` によって提供されるようなスレッドセーフな `rng` を必要とします。

他のすべてのキーワード引数 `kws...` は、`nchains` が提供されているかどうかに応じて、`DynamicHMC.mcmc_with_warmup` または `DynamicHMC.mcmc_keep_warmup` に渡されます。

# 戻り値

  * `nchains` が提供されていない場合、DynamicHMC.jl のドキュメントに要約された `NamedTuple` を返します。簡単に言うと、サンプルの行列は `exp.( result.posterior_matrix )` として抽出および変換できます。チェーンに関する統計は `DynamicHMC.Diagnostics.summarize_tree_statistics(result.tree_statistics)` で取得できます。受け入れ率がかなり高い (>0.5) ことと、サンプルの大部分が終了基準が「ターン」であることを確認したいです。詳細については、DynamicHMC.jl のドキュメントを参照してください。
  * `nchains` が提供されている場合、上記で説明した同じ `NamedTuple` の長さ `nchains` のベクトルを返します。返されたベクトルの各チェーンからのサンプルは、`DynamicHMC.stack_posterior_matrices(result)` を使用して単一の `(nsamples, nchains, length(models))` 行列にスタックできます。

# 例

```

julia import DynamicHMC import StatFormationHistories: hmc_sample import Statistics: mean

# 進捗メーターを使用して進捗を監視しながらサンプラーを実行

# テンプレート `models` と観測ヘス図 `data` を構築したと仮定

result = hmc_sample( models, data, 1000; reporter=DynamicHMC.ProgressMeterReport())

# チェーンの値は result.posterior 行列に格納されます; `result.posterior_matrix` で抽出します

# 最適化は内部で対数変換を使用し、log(θ) をサンプリングするため、指数変換が必要です。

mc*matrix = exp.( result.posterior*matrix )

# チェーンからの統計を確認できます; 高い受け入れ率 (>0.5) と大きな割合の

# 終了基準の「ターン」を確認したいです。

DynamicHMC.Diagnostics.summarize*tree*statistics(result.tree_statistics)     ハミルトンモンテカルロサンプルの長さ 1000       受け入れ率の平均: 0.92, 5/25/50/75/95%: 0.65 0.88 0.97 1.0 1.0       終了: 発散 => 0%, 最大深さ => 0%, ターン => 100%       深さ: 0 => 0%, 1 => 64%, 2 => 36%

# mc_matrix のサイズは `(length(models), nsteps)` で、各列は係数によって定義された

# SFH の独立したサンプルで、行には各パラメータのサンプルが含まれます。

mstar*tot = sum.(eachcol(mc*matrix)) # モデル化されたシステムのサンプルごとの総星質量 mc*means = mean.(eachrow(mc*matrix)) # すべてのサンプルにわたって評価された各係数の平均

# マルチスレッドを介して並列でサンプリングされた複数のチェーンの例

import Threads t*result = hmc*sample( models, data, 1000, Threads.nthreads(); reporter=DynamicHMC.ProgressMeterReport())

# 複数のチェーンを単一の行列に結合し、変換します

# 上記の `mc_matrix` と同じ方法で使用できます

mc*matrix = exp.( DynamicHMC.pool*posterior*matrices(t*result) ) ```
