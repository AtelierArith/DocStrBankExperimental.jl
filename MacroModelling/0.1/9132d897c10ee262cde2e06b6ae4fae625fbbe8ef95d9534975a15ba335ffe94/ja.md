```julia
get_conditional_forecast(
    𝓂,
    conditions;
    shocks,
    initial_state,
    periods,
    parameters,
    variables,
    conditions_in_levels,
    algorithm,
    levels,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm
)

```

内生変数とショックに対する制約を考慮した条件付き予測を返します（オプション）。デフォルトでは、値は関連する定常状態からの絶対偏差を表します（詳細は`levels`を参照）。非確率的定常状態（NSSS）は一次の解に関連し、確率的定常状態は高次の解に関連します。条件を満たす最小の二乗大きさのショックの組み合わせを見つけるために、制約付き最小化問題が解かれます。

モデルに偶発的に拘束が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `conditions` [タイプ: `Union{Matrix{Union{Nothing,Float64}}, SparseMatrixCSC{Float64}, KeyedArray{Union{Nothing,Float64}}, KeyedArray{Float64}}`]: 対応するショックを見つけるための条件。入力は複数の形式を持つことができますが、すべてのタイプのエントリに対して、最初の次元は変数に、2番目の次元は期間の数に対応します。条件は`Matrix{Union{Nothing,Float64}}`型の行列を使用して指定できます。この場合、条件は`Float64`型の行列要素であり、残りの（自由な）エントリは`nothing`です。`SparseMatrixCSC{Float64}`を入力として使用することもできます。この場合、非ゼロ要素のみが条件として考慮されます。`SparseMatrixCSC{Float64}`を使用して変数をゼロに条件付けることはできません（他の入力形式を使用してください）。条件を入力する別の方法は、`KeyedArray`を使用することです。`KeyedArray{Union{Nothing,Float64}}`を使用することができ、`Matrix{Union{Nothing,Float64}}`と同様に、`Float64`型のすべてのエントリが条件として認識され、他のすべてのエントリは`nothing`でなければなりません。さらに、主軸に条件を指定する変数のサブセット（`Symbol`または`String`型）を指定でき、他のすべての変数は自由と見なされます。`KeyedArray{Float64}}`を入力として使用する場合も同様で、この場合、指定された変数の条件は`KeyedArray`で指定されたすべての期間に対して拘束されます。なぜなら、このタイプでは`nothing`エントリが許可されていないからです。

# キーワード引数

  * `shocks` [デフォルト: `nothing`, タイプ: `Union{Matrix{Union{Nothing,Float64}}, SparseMatrixCSC{Float64}, KeyedArray{Union{Nothing,Float64}}, KeyedArray{Float64}, Nothing}`]: ショックの既知の値。この引数は、ユーザーが特定のショック値を含めることを可能にします。このようにショックに制約を入れることで、内生変数に対する条件を満たす問題は、該当する期間の残りの自由なショックに制限されます。入力は複数の形式を持つことができますが、すべてのタイプのエントリに対して、最初の次元はショックに、2番目の次元は期間の数に対応します。`shocks`は`Matrix{Union{Nothing,Float64}}`型の行列を使用して指定できます。この場合、ショックは`Float64`型の行列要素であり、残りの（自由な）エントリは`nothing`です。`SparseMatrixCSC{Float64}`を入力として使用することもできます。この場合、非ゼロ要素のみが特定のショック値として考慮されます。`SparseMatrixCSC{Float64}`を使用してショックをゼロに条件付けることはできません（他の入力形式を使用してください）。既知のショックを入力する別の方法は、`KeyedArray`を使用することです。`KeyedArray{Union{Nothing,Float64}}`を使用することができ、`Matrix{Union{Nothing,Float64}}`と同様に、`Float64`型のすべてのエントリが既知のショックとして認識され、他のすべてのエントリは`nothing`でなければなりません。さらに、主軸にショックのサブセット（`Symbol`または`String`型）を指定でき、値を指定し、他のすべてのショックは自由と見なされます。`KeyedArray{Float64}}`を入力として使用する場合も同様で、この場合、指定されたショックの値は`KeyedArray`で指定されたすべての期間に対して拘束されます。なぜなら、このタイプでは`nothing`エントリが許可されていないからです。
  * `initial_state` [デフォルト: `[0.0]`, タイプ: `Union{Vector{Vector{Float64}},Vector{Float64}}`]: 初期状態はモデルの出発点を定義します。プルーニング解法の場合、初期状態は複数の状態ベクトル（`Vector{Vector{Float64}}`）として与えることができます。この場合、初期状態は非確率的定常状態からの偏差で与えなければなりません。他のすべてのケースでは、初期状態はレベルで与えなければなりません。プルーニング解法が選択され、`initial_state`が`Vector{Float64}`の場合、これは一次の初期状態ベクトルにのみ影響します。状態には、すべての変数と、存在する場合は先行または遅延の外生変数が含まれます。`get_irf(𝓂, shocks = :none, variables = :all, periods = 1)`は、すべての変数を含む`KeyedArray`を返します。
  * `periods` [デフォルト: `40`, タイプ: `Int`]: 総期間数は、ここで提供された引数の合計と、ショックまたは条件引数の最大期間の合計です。
  * `parameters` [デフォルト: `nothing`]: `nothing`が提供された場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の`Vector`、パラメータの`Symbol`または`String`と値の`Pair`の`Vector`または`Tuple`です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `variables` [デフォルト: `:all_excluding_obc`]: 結果を表示する変数。入力は、変数名を`Symbol`または`String`（例: `:y`または"y"）として渡すか、`Tuple`、`Matrix`または`Vector`の`String`または`Symbol`の形式で渡すことができます。モデルの一部でない変数は警告を引き起こします。`:all_excluding_auxilliary_and_obc`は、補助変数および偶発的に拘束された制約（obc）に関連するショックを除いたすべてのショックを含みます。`:all_excluding_obc`は、補助変数に関連するショックを除いたすべてのショックを含みます。`:all`は、すべての変数を含みます。
  * `conditions_in_levels` [デフォルト: `true`, タイプ: `Bool`]: 条件がレベルで提供されているかどうかの指標。`true`の場合、条件引数への入力から非確率的定常状態が引かれます。
  * `levels` [デフォルト: `false`, タイプ: `Bool`]: 解法に対応するレベルまたは関連する定常状態からの絶対偏差を返します（例: 高次解法のための確率的定常状態）。
  * `algorithm` [デフォルト: `:first_order`, タイプ: `Symbol`]: モデルの動的解法のためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式を解くためのアルゴリズム（`A * X ^ 2 + B * X + C = 0`）。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題の場合: `:doubling`、大きな問題の場合: `:bicgstab`, タイプ: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式を解くためのアルゴリズム（`A * X * B + C = X`）。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は、`Vector`または`Tuple`で最大2つの要素を持つことができます。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式を解くためのアルゴリズム（`A * X * A' + C = X`）。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容値を定義します。詳細については、[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数とショック、列に期間を持つ`KeyedArray`。

# 例

```jldoctest
using MacroModelling
using SparseArrays, AxisKeys

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

# cは期間1で0.01の偏差を持つように条件付けられ、yは期間2で0.02の偏差を持つように条件付けられます
conditions = KeyedArray(Matrix{Union{Nothing,Float64}}(undef,2,2),Variables = [:c,:y], Periods = 1:2)
conditions[1,1] = .01
conditions[2,2] = .02

# 期間2で2番目のショック（eps_z）が0.05の値を取るように条件付けられます
shocks = Matrix{Union{Nothing,Float64}}(undef,2,1)
shocks[1,1] = .05

get_conditional_forecast(RBC_CME, conditions, shocks = shocks, conditions_in_levels = false)
# 出力
2次元のKeyedArray(NamedDimsArray(...))で、キーは:
↓   Variables_and_shocks ∈ 9-element Vector{Symbol}
→   Periods ∈ 42-element UnitRange{Int64}
データは、9×42のMatrix{Float64}:
                (1)            (2)           …  (41)            (42)
  (:A)            0.0313639      0.0134792         0.000221372     0.000199235
  (:Pi)           0.000780257    0.00020929       -0.000146071    -0.000140137
  (:R)            0.00117156     0.00031425       -0.000219325    -0.000210417
  (:c)            0.01           0.00600605        0.00213278      0.00203751
  (:k)            0.034584       0.0477482   …     0.0397631       0.0380482
  (:y)            0.0446375      0.02              0.00129544      0.001222
  (:z_delta)      0.00025        0.000225          3.69522e-6      3.3257e-6
  (:delta_eps)    0.05           0.0               0.0             0.0
  (:eps_z)        4.61234       -2.16887           0.0             0.0

# 他の入力形式でも同じことが達成できます:
# conditions = Matrix{Union{Nothing,Float64}}(undef,7,2)
# conditions[4,1] = .01
# conditions[6,2] = .02

# SparseArraysを使用して
# conditions = spzeros(7,2)
# conditions[4,1] = .01
# conditions[6,2] = .02

# shocks = KeyedArray(Matrix{Union{Nothing,Float64}}(undef,1,1),Variables = [:delta_eps], Periods = [1])
# shocks[1,1] = .05

# SparseArraysを使用して
# shocks = spzeros(2,1)
# shocks[1,1] = .05
```
