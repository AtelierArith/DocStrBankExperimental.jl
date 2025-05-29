```
SymmetricMatrixShape(
    side_dimension::Int;
    needs_adjoint_dual::Bool = false,
)
```

`side_dimension` 行と列を持つ対称正方行列の形状オブジェクトです。

ベクトル化された形式は、行列の上部右三角部分のエントリを列ごとに（または同等に、行ごとに下部左三角部分のエントリを）含みます。

## `needs_adjoint_dual`

デフォルトでは、[`SymmetricMatrixShape`](@ref) の [`dual_shape`](@ref) も [`SymmetricMatrixShape`](@ref) です。これは、[`PSDCone`](@ref) の `LinearAlgebra.Symmetric` 行列のようなケースに当てはまります。

しかし、JuMP は `Zeros` における `LinearAlgebra.Symmetric` 行列もサポートしており、これは要素ごとの等式制約として解釈されます。対称性を利用することで、等式制約の上三角部分のみを渡します。これはプライマルには機能しますが、オフダイアゴナルの双対要素に2倍の差をもたらします。（三角形の定式化における `(i, j)` 要素の双対値は、正方行列の定式化における `(i, j)` および `(j, i)` 要素に広がるときに2で割る必要があります。）制約にこの双対の不整合がある場合は、`needs_adjoint_dual = true` に設定してください。
