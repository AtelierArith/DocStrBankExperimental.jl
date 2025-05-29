```julia
get_shock_decomposition(
    𝓂,
    data;
    parameters,
    filter,
    algorithm,
    data_in_levels,
    warmup_iterations,
    smooth,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

関連する定常状態からの絶対偏差でショック分解を返します。非確率的定常状態（NSSS）は一次の解に関連し、確率的定常状態は高次の解に関連します。偏差は、提供されたデータとモデルの解に基づいて、カルマンスムーザーまたはフィルター（`smooth`キーワード引数に依存）または逆フィルターに基づいています。データは、`data_in_levels`が`false`に設定されていない限り、デフォルトでレベルで提供されると仮定されます。

剪定された二次および剪定された三次の摂動アルゴリズムの場合、分解にはさらに「非線形性」という項が含まれます。この項は、ショックが到着した後の期間における状態間の非線形相互作用を表し、剪定された三次の場合は（剪定された二次の）状態と同時ショック間の相互作用を表します。

モデルに偶発的に拘束条件が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `data` [タイプ: `KeyedArray`]: 行に変数（`String`または`Symbol`）、列に時間を持つデータ行列

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing`が提供される場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、パラメータの`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `filter` [デフォルト: `:kalman`, タイプ: `Symbol`]: データ、モデル、およびパラメータに基づいて変数とショックを計算するために使用されるフィルター。カルマンフィルターは線形問題にのみ機能し、逆フィルター（`:inversion`）は線形および非線形モデルに機能します。非線形解法アルゴリズムが選択された場合、逆フィルターが使用されます。
  * `algorithm` [デフォルト: `:first_order`, タイプ: `Symbol`]: モデルの動力学を解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `data_in_levels` [デフォルト: `true`, タイプ: `Bool`]: データがレベルで提供されているかどうかの指標。`true`の場合、データ引数への入力から非確率的定常状態が引かれます。
  * `smooth` [デフォルト: `true`, タイプ: `Bool`]: スムーズな（`true`）またはフィルタリングされた（`false`）ショック/変数を返すかどうか。カルマンフィルターにのみ機能します。逆フィルターはフィルタリングされたショック/変数のみを返します。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, タイプ: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は`Vector`または`Tuple`で最大2要素までです。最初の（第二の）要素は、第二（第三）次の摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは第二次の摂動解のシルベスター方程式に対応します。
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数、列にショック、三次元目に期間を持つ`KeyedArray`。

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

get_shock_decomposition(RBC,simulation([:c],:,:simulate))
# output
3-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Shocks ∈ 2-element Vector{Symbol}
◪   Periods ∈ 40-element UnitRange{Int64}
And data, 4×2×40 Array{Float64, 3}:
[showing 3 of 40 slices]
[:, :, 1] ~ (:, :, 1):
        (:eps_z₍ₓ₎)   (:Initial_values)
  (:c)   0.000407252  -0.00104779
  (:k)   0.00374808   -0.0104645
  (:q)   0.00415533   -0.000807161
  (:z)   0.000603617  -1.99957e-6

[:, :, 21] ~ (:, :, 21):
        (:eps_z₍ₓ₎)  (:Initial_values)
  (:c)   0.026511    -0.000433619
  (:k)   0.25684     -0.00433108
  (:q)   0.115858    -0.000328764
  (:z)   0.0150266    0.0

[:, :, 40] ~ (:, :, 40):
        (:eps_z₍ₓ₎)  (:Initial_values)
  (:c)   0.0437976   -0.000187505
  (:k)   0.4394      -0.00187284
  (:q)   0.00985518  -0.000142164
  (:z)  -0.00366442   8.67362e-19
```
