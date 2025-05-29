```julia
struct MultivariateGMM
```

出力として多変量ガウス混合モデルを生成するレイヤーです。

# パラメータ

  * `outputs::Int64`
  * `mixtures::Int64`
  * `μ::Flux.Dense`
  * `Σ::Flux.Dense`
  * `w::Flux.Chain`
