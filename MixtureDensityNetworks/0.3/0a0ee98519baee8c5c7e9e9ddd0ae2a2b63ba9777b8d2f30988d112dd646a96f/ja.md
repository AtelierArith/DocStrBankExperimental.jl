```julia
struct UnivariateGMM
```

出力として一変量ガウス混合モデルを生成するレイヤーです。

# パラメータ

  * `μ::Flux.Dense`
  * `Σ::Flux.Dense`
  * `w::Flux.Chain`
