```julia
get_loglikelihood(
    𝓂,
    data,
    parameter_values;
    algorithm,
    filter,
    warmup_iterations,
    presample_periods,
    initial_covariance,
    filter_algorithm,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm,
    sylvester_algorithm,
    verbose
)

```

データと提供されたパラメータに基づいてモデルの対数尤度を返します。対数尤度は、逆行列またはカルマンフィルタに基づいて計算されます（`filter`キーワード引数に依存）。非線形解法アルゴリズムの場合、逆行列フィルタが使用されます。データは、変数の名前が行に、期間が列にマッチするように、`KeyedArray{Float64}`として提供されなければなりません。

この関数は微分可能であり（現時点ではカルマンフィルタのみ）、勾配ベースのサンプリングや最適化に使用できます。

モデルに偶発的な制約が存在する場合、ここでは考慮されません。

# 引数

  * `𝓂`: [`@model`](@ref)および[`@parameters`](@ref)によって作成されたオブジェクト。
  * `data` [タイプ: `KeyedArray`]: 変数（`String`または`Symbol`）が行に、時間が列にあるデータ行列
  * `parameter_values` [タイプ: `Vector`]: パラメータ値。

# キーワード引数

  * `algorithm` [デフォルト: `:first_order`, タイプ: `Symbol`]: モデルの動力学を解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `filter` [デフォルト: `:kalman`, タイプ: `Symbol`]: データ、モデル、およびパラメータに基づいて変数とショックを計算するために使用されるフィルタ。カルマンフィルタは線形問題にのみ機能し、逆行列フィルタ（`:inversion`）は線形および非線形モデルに機能します。非線形解法アルゴリズムが選択された場合、逆行列フィルタが使用されます。
  * `presample_periods` [デフォルト: `0`, タイプ: `Int`]: 対数尤度が破棄されるデータの最初の期間。
  * `initial_covariance` [デフォルト: `:theoretical`, タイプ: `Symbol`]: カルマンフィルタの共分散行列を初期化する方法を定義します。理論的な長期値（オプション`:theoretical`）または対角線上の大きな値（10.0）（オプション`:diagonal`）で初期化できます。
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, タイプ: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さな問題: `:doubling`、大きな問題: `:bicgstab`, タイプ: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は`Vector`または`Tuple`で最大2要素まで可能です。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `lyapunov_algorithm` [デフォルト: `:doubling`, タイプ: `Symbol`]: リャプノフ方程式（`A * X * A' + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については[`Tolerances`](@ref)のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * `<:AbstractFloat` 対数尤度

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

simulated_data = simulate(RBC)

get_loglikelihood(RBC, simulated_data([:k], :, :simulate), RBC.parameter_values)
# output
58.24780188977981
```
