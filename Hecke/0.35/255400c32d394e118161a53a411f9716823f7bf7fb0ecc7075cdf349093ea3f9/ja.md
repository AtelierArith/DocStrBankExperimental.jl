```
glue_map(L::ZZLat, S::ZZLat, R::ZZLat; check=true)
                       -> Tuple{TorQuadModuleMap, TorQuadModuleMap, TorQuadModuleMap}
```

与えられた三つの整数 $\mathbb Z$-ラティス `L`、`S`、`R` において、`S` と `R` は `L` の原始部分ラティスであり、`S` と `R` の階数の和が `L` の階数に等しい場合、原始拡張 $S+R \subseteq L$ の接合写像 $\gamma$ と、$\gamma$ の定義域および値域のそれぞれの判別群への包含写像を返します。

# 例

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
整数ラティスの階数 4 および次数 8
グラム行列
[12   -3    0   -3]
[-3    2   -1    0]
[ 0   -1    2    0]
[-3    0    0    2]

julia> R = kernel_lattice(M , f^2+f+1)
整数ラティスの階数 4 および次数 8
グラム行列
[ 2   -1    0    0]
[-1    2   -6    0]
[ 0   -6   30   -3]
[ 0    0   -3    2]

julia> glue, iS, iR = glue_map(M, S, R)
(Map: 有限二次モジュール -> 有限二次モジュール, Map: 有限二次モジュール -> 有限二次モジュール, Map: 有限二次モジュール -> 有限二次モジュール)

julia> is_bijective(glue)
true
```
