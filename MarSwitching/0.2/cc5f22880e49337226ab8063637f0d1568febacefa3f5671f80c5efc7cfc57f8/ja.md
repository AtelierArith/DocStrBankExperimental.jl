generate_msm(μ::Vector{Float64}, σ::Vector{Float64}, P::Matrix{Float64}, T::Int64; <keyword arguments>)

提供されたパラメータからマルコフスイッチングモデルの人工データを生成します。`y`が生成されたデータ、`s_t`が状態系列、`X`が設計行列のタプルを返します。

スイッチしないパラメータを持つためには、k回提供する必要があります。

# 引数

  * `μ::Vector{AbstractFloat}`: 各状態の切片。
  * `σ::Vector{AbstractFloat}`: 各状態の標準偏差。
  * `P::Matrix{AbstractFloat}`: 遷移行列。
  * `T::Int64`: 生成する観測値の数。
  * `β::Vector{AbstractFloat}`: スイッチング係数。（ベクトルの最初のk要素は最初の状態方程式の係数です）。
  * `β_ns::Vector{AbstractFloat}`: スイッチしない係数。
  * `δ::Vector{AbstractFloat}`: tvtp係数。
  * `tvtp_intercept::Bool`: tvtpモデルに切片を含めるかどうか。
