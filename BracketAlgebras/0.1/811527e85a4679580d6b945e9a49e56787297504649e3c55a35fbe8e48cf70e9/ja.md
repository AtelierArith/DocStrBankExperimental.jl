```
point_labels!(B::BracketAlgebra, new_labels::AbstractVector)
```

ブランケット代数 `B` のポイントラベルを更新し、結果として得られるブランケット代数を返します。`new_labels` が整数のベクトルである場合、`collect(1:n(B))` と等しいことが期待されます。

# 例

```jldoctest
julia> point_labels!(BracketAlgebra(6,3), ["a", "b", "c", "d", "e", "f"])
Bracket algebra over P^3 on 6 points with point ordering a < b < c < d < e < f and coefficient ring Integers.
```

```jldoctest
julia> point_labels!(BracketAlgebra(6,3), [2,1,3,4,5,"a"])
Bracket algebra over P^3 on 6 points with point ordering 2 < 1 < 3 < 4 < 5 < a and coefficient ring Integers.
```

```jldoctest
julia> point_labels!(BracketAlgebra(6,3), [2,1,3,4,5,6])
ERROR: When point_labels is a Vector of Integers, it must equal collect(1:n)
```
