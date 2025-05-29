```
NN(params::Parameters;
    architecture::Union{Flux.Chain, Nothing} = nothing,
    θ::Union{Vector{AbstractFloat}, Nothing} = nothing)
```

新しいフィードフォワードニューラルネットワークを作成します。

# キーワード引数

  * `architecture`: `Flux.Chain` ニューラルネットワークアーキテクチャ（オプション）
  * `θ`: ニューラルネットワークのパラメータ（オプション）
