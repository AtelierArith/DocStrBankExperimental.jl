```julia
get_non_stochastic_steady_state_residuals(
    𝓂,
    values;
    parameters,
    tol,
    verbose
)

```

与えられた値のセットに対してモデルの非確率的定常状態方程式の残差を計算します。提供されていない値は、現在のパラメータに対応する非確率的定常状態の値で埋められます。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。
  * `values` [タイプ: `Union{Vector{Float64}, Dict{Symbol, Float64}, Dict{String, Float64}, KeyedArray{Float64, 1}}`]: 非確率的定常状態方程式（キャリブレーション方程式を含む）における変数とキャリブレーションパラメータの値を含むベクター、辞書、またはKeyedArray。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing` が提供される場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、パラメータの `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `tol` [デフォルト: `Tolerances()`, タイプ: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, タイプ: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 非確率的定常状態方程式の残差の絶対値を含む `KeyedArray`。

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
    k[ss] / q[ss] = 2.5 | α
    β = 0.95
end

steady_state = SS(RBC, derivatives = false)

get_non_stochastic_steady_state_residuals(RBC, steady_state)
# output
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Equation ∈ 5-element Vector{Symbol}
And data, 5-element Vector{Float64}:
 (:Equation₁)             0.0
 (:Equation₂)             0.0
 (:Equation₃)             0.0
 (:Equation₄)             0.0
 (:CalibrationEquation₁)  0.0

get_non_stochastic_steady_state_residuals(RBC, [1.1641597, 3.0635781, 1.2254312, 0.0, 0.18157895])
# output
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Equation ∈ 5-element Vector{Symbol}
And data, 5-element Vector{Float64}:
 (:Equation₁)             2.7360991250446887e-10
 (:Equation₂)             6.199999980083248e-8
 (:Equation₃)             2.7897102183871425e-8
 (:Equation₄)             0.0
 (:CalibrationEquation₁)  8.160392850342646e-8
```
