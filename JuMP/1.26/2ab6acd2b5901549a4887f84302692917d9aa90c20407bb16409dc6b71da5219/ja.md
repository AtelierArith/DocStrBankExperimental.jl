```
lp_matrix_data(model::GenericModel{T})
```

与えられたJuMPモデルの線形計画に対して、同等の線形計画のデータを格納する[`LPMatrixData{T}`](@ref)構造体を返します。形式は次の通りです：

$$
\begin{aligned}
\min & c^\top x + c_0 \\
      & b_l \le A x \le b_u \\
      & x_l \le x \le x_u
\end{aligned}
$$

ここで、`x`の要素は連続変数、整数変数、またはバイナリ変数である可能性があります。

## フィールド

[`lp_matrix_data`](@ref)によって返される構造体は、次のフィールドを持ちます：

  * `A::SparseArrays.SparseMatrixCSC{T,Int}`: スパース行列形式の制約行列。
  * `b_lower::Vector{T}`: 行の下限の密なベクトル。欠落している場合、`typemin(T)`の値が使用されます。
  * `b_upper::Vector{T}`: 行の上限の密なベクトル。欠落している場合、`typemax(T)`の値が使用されます。
  * `x_lower::Vector{T}`: 変数の下限の密なベクトル。欠落している場合、`typemin(T)`の値が使用されます。
  * `x_upper::Vector{T}`: 変数の上限の密なベクトル。欠落している場合、`typemax(T)`の値が使用されます。
  * `c::Vector{T}`: 線形目的係数の密なベクトル。
  * `c_offset::T`: 目的関数の定数項。
  * `sense::MOI.OptimizationSense`: モデルの目的の感覚。
  * `integers::Vector{Int}`: 整数変数の列インデックスのソートされたリスト。
  * `binaries::Vector{Int}`: バイナリ変数の列インデックスのソートされたリスト。
  * `variables::Vector{GenericVariableRef{T}}`: 行列形式の列の順序に対応する[`GenericVariableRef`](@ref)のベクトル。
  * `affine_constraints::Vector{ConstraintRef}`: 行列形式の行の順序に対応する[`ConstraintRef`](@ref)のベクトル。

## 制限

[`lp_matrix_data`](@ref)によってサポートされるモデルは、意図的に線形計画に制限されています。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2] >= 0);

julia> @constraint(model, x[1] + 2 * x[2] <= 1);

julia> @objective(model, Max, x[2]);

julia> data = lp_matrix_data(model);

julia> data.A
1×2 SparseArrays.SparseMatrixCSC{Float64, Int64} with 2 stored entries:
 1.0  2.0

julia> data.b_lower
1-element Vector{Float64}:
 -Inf

julia> data.b_upper
1-element Vector{Float64}:
 1.0

julia> data.x_lower
2-element Vector{Float64}:
 0.0
 0.0

julia> data.x_upper
2-element Vector{Float64}:
 Inf
 Inf

julia> data.c
2-element Vector{Float64}:
 0.0
 1.0

julia> data.c_offset
0.0

julia> data.sense
MAX_SENSE::OptimizationSense = 1
```
