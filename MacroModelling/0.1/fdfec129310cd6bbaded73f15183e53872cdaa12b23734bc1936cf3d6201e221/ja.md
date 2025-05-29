```julia
get_correlation(
    𝓂;
    parameters,
    algorithm,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

内生変数の相関を、最初の、剪定された第二、または剪定された第三次の摂動解を使用して返します。

モデルに偶発的に拘束条件が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing` が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、またはパラメータの `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的を解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式 (`A * X ^ 2 + B * X + C = 0`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式 (`A * X * A' + C = X`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式 (`A * X * B + C = X`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は `Vector` または `Tuple` で最大2要素まで可能です。最初の（第二の）要素は、第二（第三）次の摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは第二次の摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行と列に変数を持つ `KeyedArray`。

# 例

```jldoctest part1
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end

@parameters RBC begin
    std_z = 0.01
    ρ = 0.2
    δ = 0.02
    α = 0.5
    β = 0.95
end

get_correlation(RBC)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   𝑉𝑎𝑟𝑖𝑎𝑏𝑙𝑒𝑠 ∈ 4-element Vector{Symbol}
And data, 4×4 Matrix{Float64}:
        (:c)       (:k)       (:q)       (:z)
  (:c)   1.0        0.999812   0.550168   0.314562
  (:k)   0.999812   1.0        0.533879   0.296104
  (:q)   0.550168   0.533879   1.0        0.965726
  (:z)   0.314562   0.296104   0.965726   1.0
```
