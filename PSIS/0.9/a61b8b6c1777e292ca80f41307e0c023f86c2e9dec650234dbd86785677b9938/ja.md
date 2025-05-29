```
psis(log_ratios, reff = 1.0; kwargs...) -> PSISResult
psis!(log_ratios, reff = 1.0; kwargs...) -> PSISResult
```

パレート平滑化重要度サンプリング（PSIS）ログ重みを計算します [VehtariSimpson2021](@citep)。

`psis` は平滑化されたログ重みをアウトオブプレイスで計算し、`psis!` はそれらをインプレースで平滑化します。

# 引数

  * `log_ratios`: 重要度比の対数の配列で、サイズは `(draws, [chains, [parameters...]])` です。`chains>1` は、マルコフ連鎖モンテカルロを使用して生成されたチェーンに使用されます。
  * `reff::Union{Real,AbstractArray}`: `log_ratios` の有効サンプルサイズと実際のサンプルサイズの比率 `reff = ess/(draws * chains)` で、自動相関を考慮するために使用されます。例えば、マルコフ連鎖モンテカルロによるものです。配列の場合、`log_ratios` に一致するサイズ `(parameters...,)` でなければなりません。

# キーワード

  * `warn=true`: `true` の場合、警告メッセージが表示されます。
  * `normalize=true`: `true` の場合、ログ重みはログ正規化され、`exp.(log_weights)` がサンプル次元に沿って 1 になるようにします。

# 戻り値

  * `result`: パレート平滑化の結果を含む [`PSISResult`](@ref) オブジェクト。

パレート形状パラメータ $k ≥ 0.7$ の場合、警告が発生します。詳細については [`PSISResult`](@ref) を参照し、診断プロットについては [`PSISPlots.paretoshapeplot`](@ref) を参照してください。

# 例

ここでは、標準正規分布を提案として使用して、30 の等方的なスチューデント $t$ 分布パラメータの重要度サンプリングのログ重要度比を平滑化します。

```jldoctest psis; setup = :(using Random; Random.seed!(42))
julia> using Distributions

julia> proposal, target = Normal(), TDist(7);

julia> x = rand(proposal, 1_000, 1, 30);  # (ndraws, nchains, nparams)

julia> log_ratios = @. logpdf(target, x) - logpdf(proposal, x);

julia> result = psis(log_ratios)
┌ Warning: 9 parameters had Pareto shape values 0.7 < k ≤ 1. Resulting importance sampling estimates are likely to be unstable.
└ @ PSIS ~/.julia/packages/PSIS/...
┌ Warning: 1 parameters had Pareto shape values k > 1. Corresponding importance sampling estimates are likely to be unstable and are unlikely to converge with additional samples.
└ @ PSIS ~/.julia/packages/PSIS/...
PSISResult with 1000 draws, 1 chains, and 30 parameters
Pareto shape (k) diagnostic values:
                        Count       Min. ESS
 (-Inf, 0.5]  good       7 (23.3%)  959
  (0.5, 0.7]  okay      13 (43.3%)  938
    (0.7, 1]  bad        9 (30.0%)  ——
    (1, Inf)  very bad   1 (3.3%)   ——
```

もしドローが MCMC を使用して生成された場合、[`MCMCDiagnosticTools.ess`](@extref) を使用して相対効率を計算できます。

```jldoctest psis
julia> using MCMCDiagnosticTools

julia> reff = ess(log_ratios; kind=:basic, split_chains=1, relative=true);

julia> result = psis(log_ratios, reff)
┌ Warning: 9 parameters had Pareto shape values 0.7 < k ≤ 1. Resulting importance sampling estimates are likely to be unstable.
└ @ PSIS ~/.julia/packages/PSIS/...
┌ Warning: 1 parameters had Pareto shape values k > 1. Corresponding importance sampling estimates are likely to be unstable and are unlikely to converge with additional samples.
└ @ PSIS ~/.julia/packages/PSIS/...
PSISResult with 1000 draws, 1 chains, and 30 parameters
Pareto shape (k) diagnostic values:
                        Count       Min. ESS
 (-Inf, 0.5]  good       9 (30.0%)  806
  (0.5, 0.7]  okay      11 (36.7%)  842
    (0.7, 1]  bad        9 (30.0%)  ——
    (1, Inf)  very bad   1 (3.3%)   ——
```

# 参考文献

  * [VehtariSimpson2021](@cite) Vehtari et al. JMLR 25:72 (2021).

```
