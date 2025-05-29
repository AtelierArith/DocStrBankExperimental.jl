```
DeepSplitting(nn, K=1, opt = Flux.Optimise.Adam(0.01), λs = nothing, mc_sample =  NoSampling())
```

ディープスプリッティングアルゴリズム。

# 引数

  * `nn`: [Flux.Chain](https://fluxml.ai/Flux.jl/stable/reference/models/layers/#Flux.Chain) または一般的には [functor](https://github.com/FluxML/Functors.jl)。
  * `K`: モンテカルロ積分の数。
  * `opt`: 使用するオプティマイザ。デフォルトは `Flux.Optimise.Adam(0.01)`。
  * `λs`: 学習率、順次使用される。デフォルトは `opt` から取得される単一の値。
  * `mc_sample::MCSampling` : 非局所項のモンテカルロ積分のためのサンプリング方法。`UniformSampling(a,b)`、`NormalSampling(σ_sampling, shifted)`、またはデフォルトの `NoSampling` が使用できます。

# 例

```julia
hls = d + 50 # 隠れ層のサイズ
d = 10 # サンプルのサイズ

# スキームで使用されるニューラルネットワーク
nn = Flux.Chain(Dense(d, hls, tanh),
                Dense(hls,hls,tanh),
                Dense(hls, 1, x->x^2))

alg = DeepSplitting(nn, K=10, opt = Flux.Optimise.Adam(), λs = [5e-3,1e-3],
                    mc_sample = UniformSampling(zeros(d), ones(d)) )
```
