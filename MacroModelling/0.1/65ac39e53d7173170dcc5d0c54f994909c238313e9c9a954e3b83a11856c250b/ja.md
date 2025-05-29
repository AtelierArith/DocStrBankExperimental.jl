```julia
get_solution(
    𝓂;
    parameters,
    algorithm,
    silent,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm
)

```

モデルの解を返します。線形の場合、非確率的定常状態（NSSS）とモデルの線形化された解が返されます。非線形の場合（高次摂動）には、内生変数を第二次元、状態変数、ショック、および摂動パラメータ（:Volatility）を他の次元とする多次元配列が返されます。

出力の値は、線形解の場合のNSSSを表し、その下にはそれぞれの過去の状態、ショック、および摂動パラメータからのNSSSの偏差が現在のモデル変数の値（NSSS偏差）に与える影響が示されます（摂動パラメータ = 1）。

# 引数

  * `𝓂`: [`@model`](@ref) および [`@parameters`](@ref) によって作成されたオブジェクト。

# キーワード引数

  * `parameters` [デフォルト: `nothing`]: `nothing` が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、またはパラメータ `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。
  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的解法に使用するアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式（`A * X ^ 2 + B * X + C = 0`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さい問題: `:doubling`、大きい問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式（`A * X * B + C = X`）を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は `Vector` または `Tuple` で最大2要素までです。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * `KeyedArray` は、内生変数を列として表示し、補助的な内生および外生変数（リードとラグが1を超えるため）を含みます。行および他の次元（選択した摂動順に依存）は、線形の場合のみNSSSを含み、その後に状態と外生ショックが続きます。変数名の後に付く下付き文字はタイミングを示します（例: `variable₍₋₁₎` は過去の変数を示します）。上付き文字はリードまたはラグを示します（例: `variableᴸ⁽²⁾` は2期間先の変数を示します）。変数名の後に上付き文字または下付き文字がない場合、その変数は現在のものです。

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

get_solution(RBC)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Steady_state__States__Shocks ∈ 4-element Vector{Symbol}
→   Variables ∈ 4-element Vector{Symbol}
And data, 4×4 adjoint(::Matrix{Float64}) with eltype Float64:
                   (:c)         (:k)        (:q)        (:z)
  (:Steady_state)   5.93625     47.3903      6.88406     0.0
  (:k₍₋₁₎)          0.0957964    0.956835    0.0726316  -0.0
  (:z₍₋₁₎)          0.134937     1.24187     1.37681     0.2
  (:eps_z₍ₓ₎)       0.00674687   0.0620937   0.0688406   0.01
```
