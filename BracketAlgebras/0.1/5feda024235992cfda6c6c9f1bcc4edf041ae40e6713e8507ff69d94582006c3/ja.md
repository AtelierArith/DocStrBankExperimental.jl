```
straighten(b::BracketAlgebraElem)
```

ブラケット代数要素 `b` に対して、Sturmfels 2008 のアルゴリズム 3.5.6 に従って直線化アルゴリズムを実行します。直線化アルゴリズムは、ブラケット代数要素 `b` のグレブナー削減を直線化シジゲをグレブナー基底として行います。結果は、すべての項が標準である `b` の標準形です。さらに [`straightening_sizyge`](@ref)、[`standard_violation`](@ref)、[`is_standard`](@ref) も参照してください。

# 例

```jldoctest
julia> B = BracketAlgebra(6, 2)
Bracket algebra over P^2 on 6 points with point ordering 1 < 2 < 3 < 4 < 5 < 6 and coefficient ring Integers.

julia> b = B([1,4,5])*B([1,5,6])*B([2,3,4])
[2, 3, 4][1, 5, 6][1, 4, 5]

julia> straighten(b)
[2, 5, 6][1, 4, 5][1, 3, 4] - [3, 5, 6][1, 4, 5][1, 2, 4] + [4, 5, 6][1, 4, 5][1, 2, 3]
```
