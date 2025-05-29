```
struct OLS
    X::AbstractMatrix{Float64}
    y::AbstractVector{Float64}
    betas::AbstractVector{Float64}
end 

設計行列、応答ベクトル、および推定回帰パラメータを保持する不変データ構造です。
```

# 引数

  * `X::AbstractMatrix{Float64}`: 設計行列。
  * `y::AbstractVector{Float64}`: 応答ベクトル。
  * `betas::AbstractVector{Float64}`: 回帰係数。
