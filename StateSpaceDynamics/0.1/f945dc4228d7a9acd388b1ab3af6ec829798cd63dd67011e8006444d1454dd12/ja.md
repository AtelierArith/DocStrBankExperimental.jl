```
function GaussianEmission(; output_dim::Int, μ::Vector{<:Real}=zeros(output_dim), Σ::Matrix{<:Real}=Matrix{Float64}(I, output_dim, output_dim))
```

与えられた出力次元、平均、および共分散を持つGaussianEmissionを作成する関数です。

# 引数

  * `output_dim::Int`: エミッションの出力次元
  * `μ::Vector{<:Real}=zeros(output_dim)`: ガウスの平均
  * `Σ::Matrix{<:Real}=Matrix{Float64}(I, output_dim, output_dim))`: ガウスの共分散行列

# 戻り値
