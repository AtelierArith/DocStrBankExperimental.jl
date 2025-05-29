```julia
get_solution(
    𝓂,
    parameters;
    algorithm,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm
)

```

モデルの解の構成要素を返します：非確率的定常状態（NSSS）と、解の順序に対応する解行列。返されるすべてのオブジェクトは行に変数を持ち、解行列は列に状態変数、次に高次解行列のための摂動/ボラティリティパラメータ、最後に外生的ショックを持ちます。高次の摂動行列はスパースであり、前述の要素のクロネッカー積を列として持ちます。最後の要素は、解が数値的に正確であるかどうかを示すブール値です。パラメータに対するIRFを微分する際に使用する関数です。

# 引数

  * `𝓂`: [`@model`](@ref) および [`@parameters`](@ref) によって作成されたオブジェクト。
  * `parameters` [デフォルト: `nothing`]: `nothing` が提供されると、以前に定義されたパラメータに対して解が計算されます。受け入れ可能な入力は、パラメータ値の `Vector`、またはパラメータ `Symbol` または `String` と値の `Pair` の `Vector` または `Tuple` です。新しいパラメータ値が以前に定義されたものと異なる場合、解は再計算されます。

# キーワード引数

  * `algorithm` [デフォルト: `:first_order`, 型: `Symbol`]: モデルの動的を解くためのアルゴリズム。利用可能なアルゴリズム: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [デフォルト: `:schur`, 型: `Symbol`]: 二次行列方程式 (`A * X ^ 2 + B * X + C = 0`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:schur`, `:doubling`
  * `sylvester_algorithm` [デフォルト: 問題のサイズに応じた関数、小さい問題: `:doubling`、大きい問題: `:bicgstab`, 型: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: シルベスター方程式 (`A * X * B + C = X`) を解くためのアルゴリズム。利用可能なアルゴリズム: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`。入力引数は `Vector` または `Tuple` で最大2要素まで。最初の（2番目の）要素は、2次（3次）摂動解のシルベスター方程式に対応します。1つの要素のみが提供される場合、それは2次摂動解のシルベスター方程式に対応します。
  * `tol` [デフォルト: `Tolerances()`, 型: `Tolerances`]: モデルを解くために使用されるアルゴリズムのさまざまな許容誤差を定義します。詳細については [`Tolerances`](@ref) のドキュメントを参照してください: `?Tolerances`
  * `verbose` [デフォルト: `false`, 型: `Bool`]: モデルを解くために使用されるさまざまなソルバーの結果に関する情報を印刷します（非確率的定常状態ソルバー、シルベスター方程式、リャプノフ方程式、および二次行列方程式）。

# 戻り値

  * `Tuple` は、NSSSを含む `Vector` と、1次解行列を含む `Matrix` で構成されます。高次解の場合、`SparseMatrixCSC` は高次解行列を表します。最後の要素は、提供された解の正確性を示す `Bool` です。

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

get_solution(RBC, RBC.parameter_values)
# output
([5.936252888048724, 47.39025414828808, 6.884057971014486, 0.0], 
 [0.09579643002421227 0.1349373930517757 0.006746869652588215; 
  0.9568351489231555 1.241874201151121 0.06209371005755664; 
  0.07263157894736819 1.376811594202897 0.06884057971014486; 
  0.0 0.19999999999999998 0.01], true)
```
