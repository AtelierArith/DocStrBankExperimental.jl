`optimizeSecondOrderModel(problem*name, g, H, δ, γ*1, γ*2, γ*3, r, min*grad, print*level)` この関数は二次問題の解を見つけます

```
argmin_d 1/2 d ^ T * H * d + g ^ T  * d
s.t. || d || <= r                  (1)
```

ここで、|| . || はベクトルのl2ノルムです。

この問題 (1) は、次の方程式系を解くことによって近似的に解決されます：

```
||H d*k + g + δ d*k|| <= γ*1 * min*grad           (2) 
γ*2 * ||d*k||) <=  γ*2 * r 
||d*k|| <= r 
M*k(d*k) <= - γ*3 * 0.5 * δ * ||d*k|| ^ 2 
H + δ I ≥ 0
```

解を見つけるための論理は、まず、δにおける単変数関数ϕを定義することです（(3)を参照）。次に、ϕ(δ) * ϕ(δ*prime) <= 0となるような区間[δ, δ*prime]を構築し、二分法を使用してϕ関数の根δ*mを見つけます。δ*mを使用して、d*kを次のように計算します：d*k = (H + δ_m * I) ^ {-1} (-g)。何らかの理由で区間を構築できなかったり、二分法が失敗した場合は、問題をハードケースとしてマークし、逆幾何級数法を使用してヘッセ行列の近似最小固有値を見つけ、その後、最小固有値を使用して探索方向を計算します。

# 入力：

  * `problem_name::String`。最適化される問題の名前、例えばCUTEstベンチマーク問題SCURLY10。
  * `g::Vector{Float64}`。(1)を参照。現在の反復xにおける勾配。
  * `H::Union{Matrix{Float64}, SparseMatrixCSC{Float64, Int64}, Symmetric{Float64, SparseMatrixCSC{Float64, Int64}}}`。

(1)を参照。現在の反復xにおけるヘッセ行列。

  * `δ::Float64`。(1)を参照。上記の方程式系(2)を解くためのウォームスタート値。
  * `γ_1::Float64`。(2)を参照。ステップd_kが正確な解からどれだけ近くなるべきかを指定します。
  * `γ_2::Float64`。(2)を参照。δ > 0のとき、ステップd_kが信頼領域の境界からどれだけ近くなるべきかを指定します。
  * `γ_3::Float64`。(2)を参照。探索方向のノルムに対するモデルのどれだけの削減を指定します。
  * `r::Float64`。(1)を参照。信頼領域の半径。
  * `min_grad::Float64`。(2)を参照。すべての反復における最小勾配。
  * `print_level::Float64`。ログの冗長性レベル。

# 出力：

'success*subproblem*solve::Bool'    'δ*k::Float64'。(1)、(2)、および(3)を参照。ϕ(δ*k) = 0となるような上記の方程式系の解。これを使用してd*kを計算します。    'd*k::Vector{Float64}`。(1)を参照。式(1)の解である探索方向。    'temp*total*number*factorizations::Int64'。H + δ Iのために行われたチョレスキー因子分解の総数。    'hard*case::Bool'。(2)を参照。δ*k = -λ*1(H)であるかどうかを指定します。ここで、λ*1は行列Hの最小固有値です。    'temp*total*number*factorizations*findinterval::Int64'。区間[δ, δ*prime]を見つける際にH + δ Iのために行われたチョレスキー因子分解の数。    'temp*total*number*factorizations*bisection::Int64'。二分法を行う際にH + δ Iのために行われたチョレスキー因子分解の数。    'total*number*factorizations*compute*search*direction::Int64'。d*k = (H + δ*m * I) ^ {-1} (-g)を計算する際に行われたチョレスキー因子分解の数。    'temp*total*number*factorizations*inverse*power*iteration::Int64'。ハードケースインスタンスを解く際に行われたチョレスキー因子分解の数。    temp*total*number*factorizations = temp*total*number*factorizations*findinterval

  * temp*total*number*factorizations*bisection + total*number*factorizations*compute*search_direction
  * temp*total*number*factorizations*inverse*power*iteration
