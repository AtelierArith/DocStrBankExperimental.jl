```
glue_map(L::ZZLat, S::ZZLat, R::ZZLat; check=true)
                       -> Tuple{TorQuadModuleMap, TorQuadModuleMap, TorQuadModuleMap}
```

Given three integral $\mathbb Z$-lattices `L`, `S` and `R`, with `S` and `R` primitive sublattices of `L` and such that the sum of the ranks of `S` and `R` is equal to the rank of `L`, return the glue map $\gamma$ of the primitive extension $S+R \subseteq L$, as well as the inclusion maps of the domain and codomain of $\gamma$ into the respective discriminant groups of `S` and `R`.

# Example

```jldoctest
julia> M = root_lattice(:E,8);

julia> f = matrix(QQ, 8, 8, [-1 -1  0  0  0  0  0  0;
                              1  0  0  0  0  0  0  0;
                              0  1  1  0  0  0  0  0;
                              0  0  0  1  0  0  0  0;
                              0  0  0  0  1  0  0  0;
                              0  0  0  0  0  1  1  0;
                             -2 -4 -6 -5 -4 -3 -2 -3;
                              0  0  0  0  0  0  0  1]);

julia> S = kernel_lattice(M ,f-1)
Integer lattice of rank 4 and degree 8
with gram matrix
[12   -3    0   -3]
[-3    2   -1    0]
[ 0   -1    2    0]
[-3    0    0    2]

julia> R = kernel_lattice(M , f^2+f+1)
Integer lattice of rank 4 and degree 8
with gram matrix
[ 2   -1    0    0]
[-1    2   -6    0]
[ 0   -6   30   -3]
[ 0    0   -3    2]

julia> glue, iS, iR = glue_map(M, S, R)
(Map: finite quadratic module -> finite quadratic module, Map: finite quadratic module -> finite quadratic module, Map: finite quadratic module -> finite quadratic module)

julia> is_bijective(glue)
true
```
