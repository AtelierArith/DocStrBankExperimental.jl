```
NetworkArg(
    model::BiophysicalModel
    protocol::Protocol
    params::Tuple{Vararg{String}}
    prior_range::Tuple{Vararg{Tuple{Float64,Float64}}} # プライヤの範囲 
    prior_dist::Tuple{Vararg{<:Any}}
    paralinks::Tuple{Vararg{Pair{String,<:String}}} = ()
    noise_type::String = "Gaussian" # "Rician"    
    sigma_range::Tuple{Float64, Float64}
    sigma_dist::Distribution
    nsamples::Int64
    nin::Int64
    nout::Int64
    hidden_layers::Tuple{Vararg{Int64}}
    dropoutp::Union{<:AbstractFloat, Tuple{Vararg{<:AbstractFloat}}}
    actf::Function
)
```

`NetworkArg`オブジェクトを返し、特定の生物物理モデルのニューラルネットワークモデルを構築し、トレーニングサンプルを生成するために必要なパラメータを指定します。テストネットワークアーキテクチャとトレーニングサンプルは、関数を使用することでモデリングタスクから自動的に決定できます。

```
NetworkArg(model, protocol, params, prior_range, prior_dist, paralinks, noisetype, sigma_range, sigma_dist)
```
