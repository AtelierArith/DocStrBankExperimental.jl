```
overlattice(glue_map::TorQuadModuleMap) -> ZZLat
```

与えられた $\mathbb Z$-格子の原始拡張の接着マップ $S+R \subseteq L$ に対して、`L` を返します。

# 例

```jldoctest
julia> M = root_lattice(:E,8);

julia> f = matrix(QQ, 8, 8, [ 1  0  0  0  0  0  0  0;
                              0  1  0  0  0  0  0  0;
                              1  2  4  4  3  2  1  2;
                             -2 -4 -6 -5 -4 -3 -2 -3;
                              2  4  6  4  3  2  1  3;
                             -1 -2 -3 -2 -1  0  0 -2;
                              0  0  0  0  0 -1  0  0;
                             -1 -2 -3 -3 -2 -1  0 -1]);

julia> S = kernel_lattice(M ,f-1)
整数格子のランク 4 および次数 8
グラム行列
[ 2   -1     0     0]
[-1    2    -1     0]
[ 0   -1    12   -15]
[ 0    0   -15    20]

julia> R = kernel_lattice(M , f^4+f^3+f^2+f+1)
整数格子のランク 4 および次数 8
グラム行列
[10   -4    0    1]
[-4    2   -1    0]
[ 0   -1    4   -3]
[ 1    0   -3    4]

julia> glue, iS, iR = glue_map(M, S, R);

julia> overlattice(glue) == M
true
```
