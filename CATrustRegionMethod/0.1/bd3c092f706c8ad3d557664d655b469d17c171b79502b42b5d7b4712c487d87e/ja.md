bisection(problem*name, g, H, δ, γ*1, γ*2, δ*prime, d*δ*prime, r, min*grad, print*level)

不変数関数ϕに基づいて区間[δ, δ*prime]を構築します（(3)を参照）ので、ϕ(δ) >= 0かつϕ(δ*prime) <= 0となります。

# 入力:

  * `problem_name::String`。最適化される問題の名前、例えばCUTEstベンチマーク問題SCURLY10。
  * `g::Vector{Float64}`。(1)を参照。現在の反復xにおける勾配。
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`。

(1)を参照。現在の反復xにおけるヘッセ行列。

  * 'δ::Float64'。(3)を参照。ϕ(δ) >= 0となるような区間[δ, δ_prime]の下限。
  * `γ_1::Float64`。(2)を参照。ステップd_kが正確な解からどれだけ近くなるべきかを指定します。
  * `γ_2::Float64`。(2)を参照。δ > 0のとき、ステップd_kが信頼領域の境界からどれだけ近くなるべきかを指定します。
  * 'δ*prime::Float64'。(3)を参照。ϕ(δ) <= 0となるような区間[δ, δ*prime]の上限。
  * 'd*δ*prime:Vector{Float64}`。(1)を参照。δ_primeを使用して計算された探索方向。
  * `r::Float64`。(1)を参照。信頼領域の半径。
  * `min_grad::Float64`。(2)を参照。すべての反復における最小勾配。
  * `print_level::Float64`。ログの冗長性レベル。

# 出力:

'success*bisectionl::Bool'。(3)を参照。ϕ(δ*m) = 0となるようなδ*m ∈ 区間[δ, δ*prime]が見つかったかどうかを指定します。   'δ*m::Float64'。(1)、(2)、および(3)を参照。ϕ(δ*m) = 0となるような上記の方程式系の解。   'δ::Float64'。(3)を参照。ϕ(δ) >= 0となるような区間[δ, δ*prime]の新しい下限。   'δ*prime::Float64'。(3)を参照。ϕ(δ) <= 0となるような区間[δ, δ*prime]の新しい上限。   'd*k:Vector{Float64}`。(1)を参照。(1)の解である探索方向。   'temp*total*number*factorizations*bisection::Int64'。バイセクションを行う際にH + δ Iのために行われたコレスキー因子分解の数。
