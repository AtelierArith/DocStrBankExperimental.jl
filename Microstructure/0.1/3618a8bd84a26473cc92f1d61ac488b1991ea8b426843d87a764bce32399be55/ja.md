```
Noisemodel(logpdf::Function, 
sigma_start::Float64, 
sigma_range::Tuple{Float64,Float64}, 
proposal::Distribution)
```

測定の対数尤度を計算するための `logpdf` 関数を持つ Noisemodel オブジェクトを返します（これを `logp_gauss` と `logp_rician` の間に設定します）、`sigma_start` はノイズレベルの開始値、`sigma_range` は事前範囲、`proposal` は MCMC サンプリングのための分布です。

# 例

```julia-repl
julia> Noisemodel()
Noisemodel(Microstructure.logp_gauss, 0.01, (0.005, 0.1), Distributions.Normal{Float64}(μ=0.0, σ=0.005))
```

```julia-repl
julia> Noisemodel(logpdf = logp_rician, sigma_start = 0.02, proposal = Normal(0,0.001))
Noisemodel(Microstructure.logp_rician, 0.02, (0.005, 0.1), Normal{Float64}(μ=0.0, σ=0.001))
```
