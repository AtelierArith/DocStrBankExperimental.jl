```julia
get_conditional_variance_decomposition(
    𝓂;
    periods,
    parameters,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm
)

```

内生変数の条件付き分散分解をショックに関して線形化された解を用いて返します。

モデルに偶発的に制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `periods` [デフォルト: `[1:20...,Inf]`, 型: `Union{Vector{Int},Vector{Float64},UnitRange{Int64}}`]: 条件付き分散分解を計算する期間のベクトル。ベクトルに `Inf` が含まれている場合、無条件分散分解も計算されます（[`get_variance_decomposition`](@ref) と同じ出力）。
  * `parameters` [デフォルト: `nothing`]: `nothing` が提供された場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、パラメータ `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式を解くためのアルゴリズム（`A * X ^ 2 + B * X + C = 0`）。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式を解くためのアルゴリズム（`A * X * A' + C = X`）。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については、[`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数、列にショック、3次元目に期間を持つ `KeyedArray`。

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

get_conditional_variance_decomposition(RBC_CME)
# output
3-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 7-element Vector{Symbol}
→   Shocks ∈ 2-element Vector{Symbol}
◪   Periods ∈ 21-element Vector{Float64}
And data, 7×2×21 Array{Float64, 3}:
[showing 3 of 21 slices]
[:, :, 1] ~ (:, :, 1.0):
              (:delta_eps)  (:eps_z)
  (:A)         0.0           1.0
  (:Pi)        0.00158668    0.998413
  (:R)         0.00158668    0.998413
  (:c)         0.0277348     0.972265
  (:k)         0.00869568    0.991304
  (:y)         0.0           1.0
  (:z_delta)   1.0           0.0

[:, :, 11] ~ (:, :, 11.0):
              (:delta_eps)  (:eps_z)
  (:A)         5.88653e-32   1.0
  (:Pi)        0.0245641     0.975436
  (:R)         0.0245641     0.975436
  (:c)         0.0175249     0.982475
  (:k)         0.00869568    0.991304
  (:y)         7.63511e-5    0.999924
  (:z_delta)   1.0           0.0

[:, :, 21] ~ (:, :, Inf):
              (:delta_eps)  (:eps_z)
  (:A)         9.6461e-31    1.0
  (:Pi)        0.0156771     0.984323
  (:R)         0.0156771     0.984323
  (:c)         0.0134672     0.986533
  (:k)         0.00869568    0.991304
  (:y)         0.000313462   0.999687
  (:z_delta)   1.0           0.0
```
