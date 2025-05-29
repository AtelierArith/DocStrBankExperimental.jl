```
point_ordering(B::BracketAlgebra)
```

ブランケット代数 `B` における n 点の順序を返し、それが表形式の順序を誘導します。

# 例

```jldoctest
julia> point_ordering(BracketAlgebra(6,3,[2,1,3,4,5,6]))
6-element Vector{Int64}:
 2
 1
 3
 4
 5
 6
```
