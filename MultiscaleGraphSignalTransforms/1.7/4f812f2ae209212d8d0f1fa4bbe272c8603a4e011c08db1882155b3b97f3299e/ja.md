```
K_functional(𝐩::Vector{Float64}, 𝐪::Vector{Float64}, 𝚽::Matrix{Float64},
             ∇𝚽::Matrix{Float64}, 𝛌::Vector{Float64}; length::Any = 1,
             T::Any = :Inf, dt::Float64 = 0.5/maximum(𝛌), tol::Float64 = 1e-5)
```

は、グラフ上の2つのベクトル測度 𝐩 と 𝐪 の間の K_functional を計算します。

# 入力引数

  * `𝐩::Vector{Float64}`: ソースベクトル測度。
  * `𝐪::Vector{Float64}`: 目的ベクトル測度。
  * `𝚽::Matrix{Float64}`: 重み付けされていないグラフラプラシアンの固有ベクトルの行列。
  * `∇𝚽::Matrix{Float64}`: 重み付けされていないグラフラプラシアンの固有ベクトルの勾配。
  * `𝛌::Vector{Float64}`: 固有値のベクトル。
  * `length::Any`: エッジの長さのベクトル（デフォルト: 1 は重み付けされていないグラフを表します）
  * `T::Any`: K_functional における停止時間 T（デフォルト: :Inf）
  * `tol::Float64`: 収束のための許容誤差（デフォルト: 1e-5）

# 出力引数

  * `K::Float64`: TSD 距離 d_{TSD}(p, q; T)。
  * `E::Float64`: 絶対誤差の推定上限。一般に、 `E <= tol * norm(K)` です。
