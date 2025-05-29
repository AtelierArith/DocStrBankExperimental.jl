```julia
get_moments(
    𝓂;
    parameters,
    non_stochastic_steady_state,
    mean,
    standard_deviation,
    variance,
    covariance,
    variables,
    derivatives,
    parameter_derivatives,
    algorithm,
    silent,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

内生変数の第一および第二モーメントを、第一、剪定された第二、または剪定された第三次の摂動解を使用して返します。デフォルトでは、非確率的定常状態（NSSS）と標準偏差を返しますが、分散および共分散行列をオプションで返すこともできます。モーメントの導関数（共分散を除く）も、`derivatives`を`true`に設定することで提供できます。

モデルに偶発的に拘束が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing`が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、またはパラメータの`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `non_stochastic_steady_state` [デフォルト: `true`, 型: `Bool`]: 内生変数のSSを返すスイッチ
  * `mean` [デフォルト: `false`, 型: `Bool`]: 内生変数の平均を返すスイッチ（線形化された解の平均はNSSSです）
  * `standard_deviation` [デフォルト: `true`, 型: `Bool`]: 内生変数の標準偏差を返すスイッチ
  * `variance` [デフォルト: `false`, 型: `Bool`]: 内生変数の分散を返すスイッチ
  * `covariance` [デフォルト: `false`, 型: `Bool`]: 内生変数の共分散行列を返すスイッチ
  * `variables` [デフォルト: `:all_excluding_obc`]: 結果を表示する変数。入力は、変数名を`Symbol`または`String`（例: `:y`または"y"）として渡すか、`Tuple`、`Matrix`または`Vector`の`String`または`Symbol`です。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に拘束された変数に関連するショックを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するショックを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `derivatives` [デフォルト: `true`, 型: `Bool`]: パラメータに関する導関数を計算します。
  * `parameter_derivatives` [デフォルト: :all]: 偏導関数を計算するパラメータ。入力は、パラメータ名を`Symbol`または`String`（例: `:alpha`、または"alpha"）として渡すか、`Tuple`、`Matrix`または`Vector`の`String`または`Symbol`です。`:all`はすべてのパラメータを含みます。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的解を求めるアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, 型: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は、`Vector`または`Tuple`の最大2要素までです。最初の（第二の）要素は、第二（第三）次の摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは第二次の摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については、[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 選択されたモーメントを含む`Dict{Symbol,KeyedArray}`。すべてのモーメントは行として変数を持ち、最初の列にモーメントがあり、その後にパラメータに関する偏導関数が続きます。

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

moments = get_moments(RBC);

moments[:non_stochastic_steady_state]
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Steady_state_and_∂steady_state∂parameter ∈ 6-element Vector{Symbol}
And data, 4×6 Matrix{Float64}:
        (:Steady_state)  (:std_z)  (:ρ)     (:δ)      (:α)       (:β)
  (:c)   5.93625          0.0       0.0   -116.072    55.786     76.1014
  (:k)  47.3903           0.0       0.0  -1304.95    555.264   1445.93
  (:q)   6.88406          0.0       0.0    -94.7805   66.8912   105.02
  (:z)   0.0              0.0       0.0      0.0       0.0        0.0
```

```jldoctest part1
moments[:standard_deviation]
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Standard_deviation_and_∂standard_deviation∂parameter ∈ 6-element Vector{Symbol}
And data, 4×6 Matrix{Float64}:
        (:Standard_deviation)  (:std_z)  …  (:δ)       (:α)       (:β)
  (:c)   0.0266642              2.66642     -0.384359   0.2626     0.144789
  (:k)   0.264677              26.4677      -5.74194    2.99332    6.30323
  (:q)   0.0739325              7.39325     -0.974722   0.726551   1.08
  (:z)   0.0102062              1.02062      0.0        0.0        0.0
```
