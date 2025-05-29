```
tuningselect(s::Matrix{Float64}, obs::Int, λ::AbstractVector{T}; γ::Real=0.0) where {T}
```

EBICを使用してグラフィカルラッソの最適な正則化パラメータ`λ`を選択します。

# 引数

  * `s::Matrix{Float64}`: 統計的共分散行列。
  * `obs::Int`: 観測数。
  * `λ::AbstractVector{T}`: テストする正則化パラメータのベクトル。
  * `γ::Real=0.0`: EBIC調整パラメータ。（オプション）

# 戻り値

  * `T`: 入力ベクトル`λ`からの最適な正則化パラメータ。
