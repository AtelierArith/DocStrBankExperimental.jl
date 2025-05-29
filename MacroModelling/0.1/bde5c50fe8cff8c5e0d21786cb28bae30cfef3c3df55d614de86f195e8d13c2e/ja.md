```julia
get_irf(
    𝓂;
    periods,
    algorithm,
    parameters,
    variables,
    shocks,
    negative_shock,
    generalised_irf,
    initial_state,
    levels,
    shock_size,
    ignore_obc,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

モデルのインパルス応答関数（IRF）を返します。デフォルトでは、値は関連する定常状態からの絶対偏差を表します（詳細は`levels`を参照）。非確率的定常状態（NSSS）は一次解に関連し、確率的定常状態は高次解に関連します。

モデルに時折制約があり、`ignore_obc = false`の場合、それらはショックを使用して強制されます。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# キーワード引数

  * `periods` [デフォルト: `40`, 型: `Int`]: 出力を計算する期間の数。ショックの行列が提供された場合、periodsはショックの系列の後に出力が続く期間の数を定義します。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的解法のためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `parameters` [デフォルト: `nothing`]: `nothing`が提供された場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、パラメータ`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `variables` [デフォルト: `:all_excluding_obc`]: 結果を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`または`Vector`の`String`または`Symbol`です。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および時折制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `shocks` [デフォルト: `:all_excluding_obc`]: IRFを計算するショック。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡されるショック名、または`Tuple`、`Matrix`または`Vector`の`String`または`Symbol`です。`:simulate`は、すべてのショックのランダム抽出をトリガーします（時折制約（obc）に関連するショックを除く）。`:all_excluding_obc`は、obcに関連するものを除くすべてのショックを含みます。`:all`はobcに関連するショックも含みます。ショックの系列は、ショック（`Symbol`または`String`）が行、期間が列の`Matrix{Float64}`または`KeyedArray{Float64}`として渡すことができます。シミュレーションの期間は、入力の期間次元の長さ+ `periods`で定義された期間の数に対応します。ショックの系列が`KeyedArray{Float64}`として入力される場合、行に有効なショック名の`Symbol`を付けることを確認してください。モデルの一部でないショックは警告を引き起こします。`:none`は`initial_state`と組み合わせて決定論的シミュレーションに使用できます。
  * `negative_shock` [デフォルト: `false`, 型: `Bool`]: 負のショックのためのIRFを計算します。
  * `generalised_irf` [デフォルト: `false`, 型: `Bool`]: 一般化されたIRFを計算します。非線形（高次摂動）解のみに関連します。偏差の基準定常状態は確率的定常状態です。`initial_state`は一般化されたIRFには影響しません。一般化されたIRFでは時折制約は尊重されません。
  * `initial_state` [デフォルト: `[0.0]`, 型: `Union{Vector{Vector{Float64}},Vector{Float64}}`]: 初期状態はモデルの出発点を定義します。プルーニング解法アルゴリズムの場合、初期状態は複数の状態ベクトル（`Vector{Vector{Float64}}`）として与えることができます。この場合、初期状態は非確率的定常状態からの偏差で与えなければなりません。他のすべてのケースでは、初期状態はレベルで与えなければなりません。プルーニング解法アルゴリズムが選択され、`initial_state`が`Vector{Float64}`の場合、これは一次初期状態ベクトルにのみ影響します。状態には、すべての変数と、存在する場合は先行または遅延の外生変数が含まれます。`get_irf(𝓂, shocks = :none, variables = :all, periods = 1)`は、すべての変数を持つ`KeyedArray`を返します。
  * `levels` [デフォルト: `false`, 型: `Bool`]: 解法アルゴリズムに対応するレベルまたは関連する定常状態からの絶対偏差を返します（例: 高次解法アルゴリズムの確率的定常状態）。
  * `shock_size` [デフォルト: `1`, 型: `Real`]: ショックのサイズに影響します（`:none`に設定されていない限り）。
  * `ignore_obc` [デフォルト: `false`, 型: `Bool`]: 時折制約を無視してモデルを解きます。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さい問題: `:doubling`、大きい問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は`Vector`または`Tuple`で最大2要素までです。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については、[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数、列に期間、3次元目にショックを持つ`KeyedArray`。

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

get_irf(RBC)
# output
3-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Periods ∈ 40-element UnitRange{Int64}
◪   Shocks ∈ 1-element Vector{Symbol}
And data, 4×40×1 Array{Float64, 3}:
[:, :, 1] ~ (:, :, :eps_z):
        (1)           (2)           …  (39)            (40)
  (:c)    0.00674687    0.00729773        0.00146962      0.00140619
  (:k)    0.0620937     0.0718322         0.0146789       0.0140453
  (:q)    0.0688406     0.0182781         0.00111425      0.00106615
  (:z)    0.01          0.002             2.74878e-29     5.49756e-30
```
