```
sample(model, AIS(N), Ns[; optional args])
sample(model, AIS(N), MCMCThreads(), Ns, Nc[; optional keyword args])
sample(model, AIS(N), MCMCDistributed(), Ns, Nc[; optional keyword args])
```

# 一般事項

この関数はアフィン不変MCMCサンプラーを実行し、各パラメータに対して`Particles`オブジェクトを返します。必須のパラメータは次のとおりです。

`model`: `AbstractDensity`のサブタイプ。`ApproxPosterior`、`ApproxKernelizedPosterior`、`CommonLogDensity`を参照してください。

`N`: アンサンブル内の粒子の数。この粒子は新しいサンプルを生成するために進化します。

`Ns`: 記録する必要があるサンプルの総数。

`Nc`: MCMCThreadsまたはMCMCDistributedが有効な場合に並行して実行するチェーンの総数。

利用可能なオプション引数は次のとおりです。

`discard_initial`: サンプルを保存する前に破棄するmcmc粒子の数。

`ntransitions`: 各サンプル間の粒子ごとのmcmcステップの数。

`retry_sampling`: コスト（または対数密度）が±∞またはNaNである初期粒子を再サンプリングするための最大試行回数。

`progress`: 冗長性を無効にするためのブール値。

# `CommonLogDensity`の最小例:

```julia
using KissABC
D = CommonLogDensity(
    2, #パラメータの数
    rng -> randn(rng, 2), # 初期サンプリング戦略
    x -> -100 * (x[1] - x[2]^2)^2 - (x[2] - 1)^2, # ローゼンブロックバナナの対数密度
)
res = sample(D, AIS(50), 1000, ntransitions = 100, discard_initial = 500, progress = false)
println(res)
```

出力:

```
Particles{Float64,1000}[1.43 ± 1.4, 0.99 ± 0.67]
```

# `ApproxKernelizedPosterior`（`ApproxPosterior`）の最小例

```julia
using KissABC
prior = Uniform(-10, 10) # パラメータの事前分布
sim(μ) = μ + rand((randn() * 0.1, randn())) # シミュレータ関数
cost(x) = abs(sim(x) - 0.0) # シミュレーションをターゲットデータと比較するためのコスト関数。この場合は単に'0'
plan = ApproxPosterior(prior, cost, 0.01) # 対数事後密度の近似モデル（ABC）
#                                           ApproxKernelizedPosteriorは同様に使用できます
res = sample(plan, AIS(100), 2000, discard_initial = 10000, progress = false)
println(res)
```

出力:

```
0.0 ± 0.46
```
