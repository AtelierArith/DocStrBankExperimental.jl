```
HermitianMatrixShape(
    side_dimension::Int;
    needs_adjoint_dual::Bool = false,
)
```

`side_dimension` 行と列を持つエルミート正方行列の形状オブジェクトです。

ベクトル化された形式は [`MOI.HermitianPositiveSemidefiniteConeTriangle`](@ref) に対応します。

## `needs_adjoint_dual`

デフォルトでは、[`HermitianMatrixShape`](@ref) の [`dual_shape`](@ref) も [`HermitianMatrixShape`](@ref) です。これは、[`HermitianPSDCone`](@ref) の `LinearAlgebra.Hermitian` 行列のようなケースに当てはまります。

しかし、JuMP は `Zeros` における `LinearAlgebra.Hermitian` 行列もサポートしており、これは要素ごとの等式制約として解釈されます。対称性を利用することで、等式制約の上三角部分のみを渡します。これはプライマルには機能しますが、オフダイアゴナルの双対要素において2倍の差をもたらします。（三角形の定式化における `(i, j)` 要素の双対値は、正方行列の定式化における `(i, j)` および `(j, i)` 要素に広げる際に2で割る必要があります。）制約にこの双対の不整合がある場合は、`needs_adjoint_dual = true` に設定してください。
