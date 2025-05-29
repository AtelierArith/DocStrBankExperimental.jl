```julia
get_autocorrelation(
    𝓂;
    autocorrelation_periods,
    parameters,
    algorithm,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

内生変数の自己相関を、最初の、剪定された第二、または剪定された第三の順序の摂動解を使用して返します。

モデルに偶発的に拘束が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `autocorrelation_periods` [デフォルト: `1:5`, 型: `UnitRange{Int}`]: 自己相関を返す期間
  * `parameters` [デフォルト: `nothing`]: `nothing` が提供される場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、パラメータ `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的を解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式を解くためのアルゴリズム (`A * X ^ 2 + B * X + C = 0`)。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式を解くためのアルゴリズム (`A * X * A' + C = X`)。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式を解くためのアルゴリズム (`A * X * B + C = X`)。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は `Vector` または `Tuple` で最大2要素まで。最初の（第二の）要素は第二（第三）順序の摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは第二順序の摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数、列に自己相関期間を持つ `KeyedArray`。

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

get_autocorrelation(RBC)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Autocorrelation_periods ∈ 5-element UnitRange{Int64}
And data, 4×5 Matrix{Float64}:
        (1)         (2)         (3)         (4)         (5)
  (:c)    0.966974    0.927263    0.887643    0.849409    0.812761
  (:k)    0.971015    0.931937    0.892277    0.853876    0.817041
  (:q)    0.32237     0.181562    0.148347    0.136867    0.129944
  (:z)    0.2         0.04        0.008       0.0016      0.00032
```
