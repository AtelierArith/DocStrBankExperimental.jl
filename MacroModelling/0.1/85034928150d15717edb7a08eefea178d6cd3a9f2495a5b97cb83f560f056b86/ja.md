```julia
get_steady_state(
    𝓂;
    parameters,
    derivatives,
    stochastic,
    algorithm,
    parameter_derivatives,
    return_variables_only,
    verbose,
    silent,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm
)

```

非確率的な定常状態、キャリブレーションされたパラメータ、およびモデルパラメータに関する導関数を返します。

# 引数

  * `𝓂`: [`@model`](@ref) と [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing` が提供された場合、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、パラメータ `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `derivatives` [デフォルト: `true`, 型: `Bool`]: パラメータに関する導関数を計算します。
  * `parameter_derivatives` [デフォルト: :all]: 部分導関数を計算するパラメータ。入力は、`Symbol` または `String`（例: `:alpha` または "alpha"）として渡されるパラメータ名、または `Tuple`、`Matrix` または `Vector` の `String` または `Symbol` です。`:all` はすべてのパラメータを含みます。
  * `stochastic` [デフォルト: `false`, 型: `Bool`]: 他の高次の摂動アルゴリズムが `algorithm` に提供されていない場合、2次の摂動を使用して確率的な定常状態を返します。
  * `return_variables_only` [デフォルト: `false`, 型: `Bool`]: キャリブレーションされたパラメータではなく、変数のみを返します。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的解法に使用するアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式 (`A * X ^ 2 + B * X + C = 0`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さい問題: `:doubling`、大きい問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式 (`A * X * B + C = X`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は `Vector` または `Tuple` で最大2要素までです。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供された場合、それは2次摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * 行に変数を持つ `KeyedArray`。列は（非確率的な）定常状態と導関数が取られるパラメータを示します。

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

get_steady_state(RBC)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables_and_calibrated_parameters ∈ 4-element Vector{Symbol}
→   Steady_state_and_∂steady_state∂parameter ∈ 6-element Vector{Symbol}
And data, 4×6 Matrix{Float64}:
        (:Steady_state)  (:std_z)  (:ρ)     (:δ)      (:α)       (:β)
  (:c)   5.93625          0.0       0.0   -116.072    55.786     76.1014
  (:k)  47.3903           0.0       0.0  -1304.95    555.264   1445.93
  (:q)   6.88406          0.0       0.0    -94.7805   66.8912   105.02
  (:z)   0.0              0.0       0.0      0.0       0.0        0.0
```
