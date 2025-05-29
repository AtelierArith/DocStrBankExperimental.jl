```
Sampler(
    params::Tuple{Vararg{String}},
    prior_range::Tuple{Vararg{Tuple{Float64, Float64}}}, 
    proposal::Tuple{Vararg{<:Any}},
    paralinks::Tuple{Vararg{Pair{String}}}, 
    nsamples::Int64 
    burnin::Int64
    thinning::Int64 
)
```

生物物理モデルのためのサンプラータイプオブジェクトを返します。

# 例

```julia-repl
julia>Sampler(
    params = ("axon.da","axon.dpara","extra.dperp_frac","fracs"),
    prior_range = ((1.0e-7,1.0e-5),(0.01e-9,0.9e-9),(0.0, 1.0),(0.0,1.0)),
    proposal = (Normal(0,0.25e-6), Normal(0,0.025e-9), Normal(0,0.05), MvNormal([0.0025 0 0;0 0.0001 0; 0 0 0.0001])),
    paralinks = ("axon.d0" => "axon.dpara", "extra.dpara" => "axon.dpara"),
    nsamples = 70000,
    burnin = 20000
)
Sampler(("axon.da", "axon.dpara", "extra.dperp_frac", "fracs"), ((1.0e-7, 1.0e-5), (1.0e-11, 9.0e-10), (0.0, 1.0), (0.0, 1.0)), (Normal{Float64}(μ=0.0, σ=2.5e-7), Normal{Float64}(μ=0.0, σ=2.5e-11), Normal{Float64}(μ=0.0, σ=0.05), ZeroMeanFullNormal(
dim: 3
μ: Zeros(3)
Σ: [0.0025 0.0 0.0; 0.0 0.0001 0.0; 0.0 0.0 0.0001]
)
), ("axon.d0" => "axon.dpara", "extra.dpara" => "axon.dpara"), 70000, 20000, 1)
```
