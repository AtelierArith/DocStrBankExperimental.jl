```
torsion_free_rank(A::FinGenAbGroup) -> Int
```

$$
A
$$

のトーションフリーランク、すなわち、$\mathbf{Q}$-ベクトル空間$A \otimes_{\mathbf Z} \mathbf Q$の次元を返します。

[`rank`](@ref)も参照してください。

# 例

```jldoctest
julia> G = abelian_group(5,0)
Z/5 x Z

julia> torsion_free_rank(G)
1

julia> rank(G)
2
```
