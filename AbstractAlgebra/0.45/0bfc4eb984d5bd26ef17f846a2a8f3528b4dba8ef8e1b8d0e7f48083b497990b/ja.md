```
diagonal_matrix(x::NCRingElement, m::Int, [n::Int])
```

$$
R
$$

上の $m \times n$ 行列を返し、主対角線上に `x` があり、それ以外はゼロです。`n` が指定されていない場合、デフォルトで `m` になります。

# 例

```jldoctest
julia> diagonal_matrix(ZZ(2), 2, 3)
[2   0   0]
[0   2   0]

julia> diagonal_matrix(QQ(-1), 3)
[-1//1    0//1    0//1]
[ 0//1   -1//1    0//1]
[ 0//1    0//1   -1//1]
```
