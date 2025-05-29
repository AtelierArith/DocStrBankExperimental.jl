```julia
get_statistics(
    𝓂,
    parameter_values;
    parameters,
    non_stochastic_steady_state,
    mean,
    standard_deviation,
    variance,
    covariance,
    autocorrelation,
    autocorrelation_periods,
    algorithm,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

内生変数の第一および第二モーメントを、線形化された解または剪定された第二または第三次の摂動解を使用して返します。デフォルトでは、非確率的定常状態（NSSS）および標準偏差を含む`Dict`を返しますが、分散および共分散行列も返すことができます。値は、特定のモーメントのために指定された順序で返されます。パラメータに対するモデルモーメントを微分する際に使用する関数です。

モデルに偶発的に束縛される制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `parameter_values` [タイプ: `Vector`]: パラメータの値。`parameter_names`が明示的に定義されていない場合、`parameter_values`はパラメータに対応し、`@parameters`ブロックで宣言されたパラメータの順序に従うと見なされます。

# キーワード引数

  * `parameters` [タイプ: `Vector{Symbol}`]: `parameter_values`と同じ順序の対応する名前。
  * `non_stochastic_steady_state` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数のNSSSを表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `mean` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数の平均を表示する変数（線形化された解の平均はNSSSです）。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `standard_deviation` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数の標準偏差を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `variance` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数の分散を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `covariance` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数の共分散を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `autocorrelation` [デフォルト: `Symbol[]`, タイプ: `Union{Symbol_input,String_input}`]: 選択された変数の自己相関を表示する変数。入力は、`Symbol`または`String`（例: `:y`または"y"）として渡される変数名、または`Tuple`、`Matrix`、または`Vector`の`String`または`Symbol`のいずれかです。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に束縛される制約（obc）に関連するものを除くすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するものを除くすべてのショックを含みます。`:all`はすべての変数を含みます。
  * `autocorrelation_periods` [デフォルト: `1:5`, タイプ = `UnitRange{Int}`]: 選択された変数の自己相関を返す期間
  * `algorithm` [デフォルト: `:first_order`, タイプ: `Symbol`]: モデルの動的解を求めるためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題の場合: `:doubling`、大きな問題の場合: `:bicgstab`, タイプ: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は、`Vector`または`Tuple`の最大2要素まで可能です。最初の（第二の）要素は、第二（第三）次の摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは第二次の摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については、[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 統計の名前と対応するベクトル（NSSS、平均、標準偏差、分散）または行列（共分散、自己相関）を含む`Dict`。

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

get_statistics(RBC, RBC.parameter_values, parameters = RBC.parameters, standard_deviation = RBC.var)
# output
Dict{Symbol, AbstractArray{Float64}} with 1 entry:
  :standard_deviation => [0.0266642, 0.264677, 0.0739325, 0.0102062]
```
