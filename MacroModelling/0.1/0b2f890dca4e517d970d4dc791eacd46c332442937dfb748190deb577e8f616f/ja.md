```julia
get_variance_decomposition(
    𝓂;
    parameters,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm
)

```

内生変数の分散分解をショックに関して線形化された解を用いて返します。

モデルに偶発的な制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing` が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、パラメータの `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式 (`A * X ^ 2 + B * X + C = 0`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式 (`A * X * A' + C = X`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数、列にショックを持つ `KeyedArray`。

# 例

```jldoctest part1
using MacroModelling

@model RBC_CME begin
    y[0]=A[0]*k[-1]^alpha
    1/c[0]=beta*1/c[1]*(alpha*A[1]*k[0]^(alpha-1)+(1-delta))
    1/c[0]=beta*1/c[1]*(R[0]/Pi[+1])
    R[0] * beta =(Pi[0]/Pibar)^phi_pi
    A[0]*k[-1]^alpha=c[0]+k[0]-(1-delta*z_delta[0])*k[-1]
    z_delta[0] = 1 - rho_z_delta + rho_z_delta * z_delta[-1] + std_z_delta * delta_eps[x]
    A[0] = 1 - rhoz + rhoz * A[-1]  + std_eps * eps_z[x]
end

@parameters RBC_CME begin
    alpha = .157
    beta = .999
    delta = .0226
    Pibar = 1.0008
    phi_pi = 1.5
    rhoz = .9
    std_eps = .0068
    rho_z_delta = .9
    std_z_delta = .005
end

get_variance_decomposition(RBC_CME)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 7-element Vector{Symbol}
→   Shocks ∈ 2-element Vector{Symbol}
And data, 7×2 Matrix{Float64}:
              (:delta_eps)  (:eps_z)
  (:A)         9.78485e-31   1.0
  (:Pi)        0.0156771     0.984323
  (:R)         0.0156771     0.984323
  (:c)         0.0134672     0.986533
  (:k)         0.00869568    0.991304
  (:y)         0.000313462   0.999687
  (:z_delta)   1.0           0.0
```
