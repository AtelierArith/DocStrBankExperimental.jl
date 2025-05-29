```
rank(A::FinGenAbGroup) -> Int
```

$$
A
$$

のランク、すなわち$A$の最小生成集合のサイズを返します。

[`torsion_free_rank`](@ref)も参照してください。

# 例

```jldoctest
julia> G = abelian_group(5,0)
Z/5 x Z

julia> torsion_free_rank(G)
1

julia> rank(G)
2
```
