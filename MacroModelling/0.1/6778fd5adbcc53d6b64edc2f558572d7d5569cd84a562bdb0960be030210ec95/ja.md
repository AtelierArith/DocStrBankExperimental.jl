```julia
get_irf(
    𝓂,
    parameters;
    periods,
    variables,
    shocks,
    negative_shock,
    initial_state,
    levels,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm
)

```

モデルのインパルス応答関数（IRF）を返します。パラメータに対するIRFを微分する際に使用する関数です。

モデルに偶発的に束縛される制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。
  * `parameters` [タイプ: `Vector`]: パラメータ名でアルファベット順にソートされたパラメータ値。

# キーワード引数

  * `periods` [デフォルト: `40`, タイプ: `Int`]: 出力を計算する期間の数。ショックの行列が提供された場合、periodsはショックの系列の後に出力が続く期間の数を定義します。
  * `variables` [デフォルト: `:all_excluding_obc`]: 結果を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`の組み合わせです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するショックを除いたすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するショックを除いたすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `shocks` [デフォルト: `:all_excluding_obc`]: IRFを計算するショック。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡されるショック名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`の組み合わせです。`:simulate`は、すべてのショックのランダムドローをトリガーします（偶発的に束縛される制約（obc）に関連するショックを除く）。`:all_excluding_obc`は、obcに関連するショックを除いたすべてのショックを含みます。`:all`はobcに関連するショックも含みます。ショックの系列は、`Matrix{Float64}`または`KeyedArray{Float64}`を使用して、行にショック（`Symbol`または`String`）、列に期間を持つ入力として渡すことができます。シミュレーションの期間は、入力の期間次元の長さ + `periods`で定義された期間の数に対応します。ショックの系列が`KeyedArray{Float64}`として入力される場合は、行に有効なショック名の`Symbol`を付けてください。モデルの一部でないショックは警告を引き起こします。`:none`は、`initial_state`と組み合わせて決定論的シミュレーションに使用できます。
  * `negative_shock` [デフォルト: `false`, タイプ: `Bool`]: 負のショックのためのIRFを計算します。
  * `initial_state` [デフォルト: `[0.0]`, タイプ: `Vector{Float64}`]: 初期状態はモデルの出発点を定義します（偏差ではなくレベルで）。状態には、すべての変数と、存在する場合は先行または遅延の外生変数が含まれます。`get_irf(𝓂, shocks = :none, variables = :all, periods = 1)`は、すべての変数を持つ`KeyedArray`を返します。
  * `levels` [デフォルト: `false`, タイプ: `Bool`]: 解法アルゴリズムに対応する関連する定常状態からのレベルまたは絶対偏差を返します（例: 高次解法アルゴリズムの確率的定常状態）。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式を解くためのアルゴリズム（`A * X ^ 2 + B * X + C = 0`）。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については、[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 変数が行、期間が列、ショックが第3次元の`Array{<:AbstractFloat, 3}`。

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

get_irf(RBC, RBC.parameter_values)
# output
4×40×1 Array{Float64, 3}:
[:, :, 1] =
 0.00674687  0.00729773  0.00715114  0.00687615  …  0.00146962   0.00140619
 0.0620937   0.0718322   0.0712153   0.0686381      0.0146789    0.0140453
 0.0688406   0.0182781   0.00797091  0.0057232      0.00111425   0.00106615
 0.01        0.002       0.0004      8.0e-5         2.74878e-29  5.49756e-30
```
