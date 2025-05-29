```
eigTSD_Distance(P::Matrix{Float64}, 𝚽::Matrix{Float64}, 𝛌::Vector{Float64},
                Q::SparseMatrixCSC{Int64,Int64}; length::Any = 1,
                T::Any = :Inf, tol::Float64 = 1e-5)
```

は、グラフ上の P の列ベクトルの TSD 距離行列を計算します。

# 入力引数

  * `P::Matrix{Float64}`: 総質量が 0 のベクトル測定。
  * `𝚽::Matrix{Float64}`: 重み付けされていないグラフラプラシアンの固有ベクトルの行列。
  * `𝛌::Vector{Float64}`: 固有値のベクトル。
  * `Q::SparseMatrixCSC{Int64,Int64}`: 重み付けされていない入射行列。
  * `length::Any`: エッジの長さのベクトル（デフォルト: `1` は重み付けされていないグラフを表します）
  * `T::Any`: K_functional における停止時間 T（デフォルト: `:Inf`）
  * `tol::Float64`: 積分収束の許容誤差（デフォルト: `1e-5`）

# 出力引数

  * `dis::Matrix{Float64}`: 距離行列、d_{TSD}(φᵢ, φⱼ; T)。
