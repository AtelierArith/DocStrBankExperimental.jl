```
even_sublattice(L::ZZLat) -> ZZLat
```

与えられた整数 $\mathbb{Z}$-格 `L` に対して、すなわち `L` 上の二次形式が整数である場合、`L` の最大の偶部分格 `L0` を返します。

もし `L` がすでに偶であるなら、$L0 = L$ です。

# 例

```jldoctest
julia> L = integer_lattice(; gram=QQ[3 0; 0 16])
整数格のランク 2 および次数 2
グラム行列
[3    0]
[0   16]

julia> L0 = even_sublattice(L)
整数格のランク 2 および次数 2
グラム行列
[12    0]
[ 0   16]

julia> index(L, L0)
2
```
