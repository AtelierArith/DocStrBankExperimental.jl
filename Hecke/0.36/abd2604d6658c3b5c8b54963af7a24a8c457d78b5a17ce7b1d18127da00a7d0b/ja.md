```
gens_with_data(A::AbstractAssociativeAlgebra; thorough_search::Bool = false)
                                                   -> Vector, Vector, Vector
```

$$
K
$$

-代数 $A$ が与えられたとき、次の三つ組 $(G, B, w)$ を返します。

  * $$
    A
    $$

    を $K$ 上の代数として生成する `basis(A)` の部分集合 $G$、
  * (新しい) 基底 $B$ とベクトル `w::Vector{Tuple{Int, Int}}` で、`B[i] = prod(G[j]^k for (j, k) in w[i]` となるようにします。

`thorough_search` が `true` の場合、返される生成元の数は少なくなる可能性があります。これは一般的に実行時間を増加させます。生成元の数が最小であることは保証されません。

# 例

```jldoctest
julia> A = matrix_algebra(QQ, 3);

julia> G, B, w = gens_with_data(A; thorough_search = true);

julia> B[1] == prod(G[i]^j for (i, j) in w[1])
true
```
