```
predictCounterfactualOutcomes(g, nSamplesPerMixture)
predictCounterfactualOutcomes(g, nSamplesPerMixture; fidelity=100)
predictCounterfactualOutcomes(g, nSamplesPerMixture; fidelity=100, minDoT=0, maxDoT=5)
```

パラメータ

  * `g::`[`GPSLCObject`](@ref): 推論がすでに計算された`GPSLCObject`。
  * `nSamplesPerMixture::Int64`: 推定された後方パラメータの各セットから引き出す結果サンプルの数。
  * `fidelity::Int64`: 治療値のドメインをカバーするために使用する介入値の数。高いほどサンプルが多くなります。
  * `minDoT::Float64=min(g.T...)`: 使用する最も低い介入治療。デフォルトはデータ`g.T`の最も低い治療値です。
  * `maxDoT::Float64=max(g.T...)`: 使用する最も高い介入治療。デフォルトはデータ`g.T`の最も高い治療値です。

```julia
julia> ite, doT = predictCounterfactualEffects(g, 30; fidelity=100)
```

戻り値 

  * `ite::Matrix{Float64}`: サイズ`[d, n, numPosteriorSamples * nSamplesPerMixture]`の配列で、dは`fidelity`によって定義された介入値の数と`g.T`の治療の範囲です - `doTrange::Vector{Float64}`: 使用されたdoTのリスト値で、`ite`の行に一致する順序です。
