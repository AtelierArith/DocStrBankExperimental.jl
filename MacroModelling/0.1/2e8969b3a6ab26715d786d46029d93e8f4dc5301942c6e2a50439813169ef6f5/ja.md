```julia
get_estimated_shocks(
    𝓂,
    data;
    parameters,
    algorithm,
    filter,
    warmup_iterations,
    data_in_levels,
    smooth,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

与えられたデータとモデルの（非）線形解を使用して、逆フィルター（`filter`キーワード引数に依存）またはカルマンフィルターまたはスムーザー（`smooth`キーワード引数に依存）に基づいて推定されたショックを返します。データは、`data_in_levels`が`false`に設定されていない限り、デフォルトでレベルで提供されると仮定されます。

モデルに偶発的な制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `data` [タイプ: `KeyedArray`]: 行に変数（`String`または`Symbol`）、列に時間を持つデータ行列

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing`が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、パラメータの`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `algorithm` [デフォルト: `:first_order`, タイプ: `Symbol`]: モデルのダイナミクスを解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `filter` [デフォルト: `:kalman`, タイプ: `Symbol`]: データ、モデル、およびパラメータに基づいて変数とショックを計算するために使用されるフィルター。カルマンフィルターは線形問題にのみ機能し、逆フィルター（`:inversion`）は線形および非線形モデルに機能します。非線形解法アルゴリズムが選択された場合、逆フィルターが使用されます。
  * `data_in_levels` [デフォルト: `true`, タイプ: `Bool`]: データがレベルで提供されているかどうかの指標。`true`の場合、データ引数への入力は非確率的定常状態が引かれます。
  * `smooth` [デフォルト: `true`, タイプ: `Bool`]: スムーズな（`true`）またはフィルタリングされた（`false`）ショック/変数を返すかどうか。カルマンフィルターにのみ機能します。逆フィルターはフィルタリングされたショック/変数のみを返します。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, タイプ: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は`Vector`または`Tuple`で最大2要素まで可能です。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行にショック、列に期間を持つ`KeyedArray`。

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

get_estimated_shocks(RBC,simulation([:c],:,:simulate))
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Shocks ∈ 1-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
And data, 1×40 Matrix{Float64}:
               (1)          (2)         (3)         (4)         …  (37)         (38)        (39)         (40)
  (:eps_z₍ₓ₎)    0.0603617    0.614652   -0.519048    0.711454       -0.873774     1.27918    -0.929701    -0.2255
```
