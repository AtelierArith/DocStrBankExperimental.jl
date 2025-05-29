```
ConstantColoringAlgorithm{partition}  <: ADTypes.AbstractColoringAlgorithm
```

常に同じ事前計算された色のベクトルを返す着色アルゴリズム。行列の最適な着色が特定の構造（例えば、バンド行列）により事前に決定できる場合に便利です。

これはメイン関数[`coloring`](@ref)に引数として渡されますが、関連する`problem`が`:nonsymmetric`構造を持つ場合にのみ機能します。実際、対称的な着色問題の場合、迅速な圧縮解除を可能にするためには、色のベクトル以上のものが必要です。

# コンストラクタ

```
ConstantColoringAlgorithm{partition}(matrix_template, color)
ConstantColoringAlgorithm(matrix_template, color; partition=:column)
```

  * `partition::Symbol`: `:row`または`:column`のいずれか。
  * `matrix_template::AbstractMatrix`: 色のベクトルが事前計算された行列（アルゴリズムは正確に同じサイズの行列のみを受け入れます）。
  * `color::Vector{<:Integer}`: 各行または列（`partition`に応じて）に対する整数の色のベクトル。

!!! warning
    2番目のコンストラクタ（キーワード引数に基づく）は型不安定です。


行列テンプレートと色のベクトルの間の整合性を必ずしも検証するわけではなく、これはユーザーの責任です。

# 例

```jldoctest
julia> using SparseMatrixColorings, LinearAlgebra

julia> matrix_template = Diagonal(ones(Bool, 5))
5×5 Diagonal{Bool, Vector{Bool}}:
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  ⋅  1

julia> color = ones(Int, 5)  # 対角行列の着色は簡単
5-element Vector{Int64}:
 1
 1
 1
 1
 1

julia> problem = ColoringProblem(; structure=:nonsymmetric, partition=:column);

julia> algo = ConstantColoringAlgorithm(matrix_template, color; partition=:column);

julia> result = coloring(similar(matrix_template), problem, algo);

julia> column_colors(result)
5-element Vector{Int64}:
 1
 1
 1
 1
 1
```

# ADTypes 着色インターフェース

`ConstantColoringAlgorithm`は[`ADTypes.AbstractColoringAlgorithm`](@extref ADTypes.AbstractColoringAlgorithm)のサブタイプであり、次のメソッドも適用可能です（ただし、要求される着色の種類が整合していない場合はエラーになります）：

  * [`ADTypes.column_coloring`](@extref ADTypes.column_coloring)
  * [`ADTypes.row_coloring`](@extref ADTypes.row_coloring)
