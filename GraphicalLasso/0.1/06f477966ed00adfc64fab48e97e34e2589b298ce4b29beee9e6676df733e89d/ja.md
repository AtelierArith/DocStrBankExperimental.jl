```
glasso(s::Matrix{Float64}, obs::Int, λ::Real; penalizediag::Bool=true, γ::Real=0.0, tol::Float64=1e-05, verbose::Bool=true, maxiter::Int=100, winit::Matrix{Float64}=zeros(size(s)))
```

グラフィカルラッソ（glasso）アルゴリズムを適用して、スパース逆共分散行列を推定します。

# 引数

  * `s::Matrix{Float64}`: 統計的共分散行列。
  * `obs::Int`: 観測数。
  * `λ::Real`: ラッソペナルティの正則化パラメータ。
  * `penalizediag::Bool=true`: 対角成分にペナルティを課すかどうか。 (オプション)
  * `γ::Real=0.0`: EBIC調整パラメータ。 (オプション)
  * `tol::Float64=1e-05`: 収束基準の許容誤差。 (オプション)
  * `verbose::Bool=true`: trueの場合、収束情報を出力します。 (オプション)
  * `maxiter::Int=100`: 最大反復回数。 (オプション)
  * `winit::Matrix{Float64}=zeros(size(s))`: 精度行列の初期値。 (オプション)

# 戻り値

  * `NamedTuple`: フィールドを持つ名前付きタプル：

      * `W::Matrix{Float64}`: 推定された精度行列。
      * `θ::Matrix{Float64}`: 推定された逆共分散行列。
      * `ll::Float64`: 推定の対数尤度。
      * `bicval::Float64`: 推定のEBIC値。
