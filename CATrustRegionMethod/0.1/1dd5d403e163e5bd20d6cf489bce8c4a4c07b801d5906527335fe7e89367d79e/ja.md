findinterval(g, H, δ, γ*2, r, print*level)

単変数関数ϕに基づいて区間[δ, δ*prime]を構築します（(3)を参照）。ここで、ϕ(δ) >= 0およびϕ(δ*prime) <= 0です。

# 入力:

  * `g::Vector{Float64}`。(1)を参照。現在の反復点xにおける勾配。
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`。

(1)を参照。現在の反復点xにおけるヘッセ行列。

  * `δ::Float64`。(1)を参照。上記のシステム(2)を解くためのウォームスタート値。
  * `γ_2::Float64`。(2)を参照。δ > 0のとき、ステップd_kが信頼領域の境界からどれだけ近くなるべきかを指定します。
  * `r::Float64`。(1)を参照。信頼領域の半径。
  * `print_level::Float64`。ログの冗長性レベル。

# 出力:

'success*find*interval::Bool'。(3)を参照。ϕ(δ) * ϕ(δ*prime) <= 0となる区間[δ, δ*prime]を見つけたかどうかを指定します。   'δ::Float64'。(3)を参照。ϕ(δ) >= 0となる区間[δ, δ*prime]の下限。   'δ*prime::Float64'。(3)を参照。ϕ(δ) <= 0となる区間[δ, δ*prime]の上限。   'd*δ*prime:Vector{Float64}`。(1)を参照。δ*primeを使用して計算された探索方向。   'temp*total*number*factorizations*findinterval::Int64'。区間[δ, δ_prime]を見つける際にH + δ Iのために行ったコレスキー因子分解の数。
