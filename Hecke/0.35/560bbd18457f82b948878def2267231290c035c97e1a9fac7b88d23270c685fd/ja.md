```
group_algebra(K::Ring, G::Group; cached::Bool = true) -> GroupAlgebra
```

群 $G$ の群代数を環 $R$ 上で返します。この構成の省略記法は `R[G]` です。

# 例

```jldoctest
julia> QG = group_algebra(QQ, small_group(8, 5))
Group algebra
  of generic group of order 8 with multiplication table
  over rational field
```
