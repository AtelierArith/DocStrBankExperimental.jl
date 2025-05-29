```
gens(A::AbstractAssociativeAlgebra; thorough_search::Bool = false) -> Vector
```

$$
K
$$

-代数 $A$ が与えられたとき、$A$ を $K$ 上の代数として生成する `basis(A)` の部分集合を返します。

`thorough_search` が `true` の場合、返される生成元の数は少なくなる可能性があります。これは一般的に実行時間を増加させます。生成元の数が最小であることは保証されません。

[`gens_with_data`](@ref) 関数は、生成元における単語として基底を表現するための追加データを計算します。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 3);

julia> gens(A; thorough_search = true)
5-element Vector{MatAlgebraElem{QQFieldElem, QQMatrix}}:
 [1 0 0; 0 0 0; 0 0 0]
 [0 0 0; 1 0 0; 0 0 0]
 [0 0 0; 0 0 0; 1 0 0]
 [0 1 0; 0 0 0; 0 0 0]
 [0 0 1; 0 0 0; 0 0 0]
```
