```julia
get_estimated_variable_standard_deviations(
    𝓂,
    data;
    parameters,
    data_in_levels,
    smooth,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm
)

```

提供されたデータとモデルの一次解に基づいて、モデル変数のカルマンスムーザーまたはフィルター（`smooth`キーワード引数に依存）の推定値の標準偏差を返します。データはデフォルトでレベルで提供されると仮定されますが、`data_in_levels`が`false`に設定されている場合は除きます。

モデルに偶発的な制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `data` [タイプ: `KeyedArray`]: 行に変数（`String`または`Symbol`）、列に時間を持つデータ行列

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing`が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、パラメータ`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `data_in_levels` [デフォルト: `true`, タイプ: `Bool`]: データがレベルで提供されているかどうかの指標。`true`の場合、データ引数への入力から非確率的定常状態が引かれます。
  * `smooth` [デフォルト: `true`, タイプ: `Bool`]: スムーズな（`true`）またはフィルターされた（`false`）ショック/変数を返すかどうか。カルマンフィルターにのみ機能します。逆フィルターはフィルターされたショック/変数のみを返します。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に標準偏差、列に期間を持つ`KeyedArray`。

# 例

```jldoctest
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

simulation = simulate(RBC)

get_estimated_variable_standard_deviations(RBC,simulation([:c],:,:simulate))
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Standard_deviations ∈ 4-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
And data, 4×40 Matrix{Float64}:
        (1)           (2)            (3)            (4)            …  (38)            (39)            (40)
  (:c)    1.23202e-9    1.84069e-10    8.23181e-11    8.23181e-11        8.23181e-11     8.23181e-11     0.0
  (:k)    0.00509299    0.000382934    2.87922e-5     2.16484e-6         1.6131e-9       9.31323e-10     1.47255e-9
  (:q)    0.0612887     0.0046082      0.000346483    2.60515e-5         1.31709e-9      1.31709e-9      9.31323e-10
  (:z)    0.00961766    0.000723136    5.43714e-5     4.0881e-6          3.08006e-10     3.29272e-10     2.32831e-10
```
