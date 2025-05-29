```
coeff(x::FqFieldElem, n::Int) -> FqFieldElem
```

有限体 $K$ の要素 $x$ に対して、$K$ の冪基底で表現したときの $x$ の次数 $n$ の係数（基底体の要素として）を返します。

# 例

```jldoctest
julia> K, a = finite_field(9, "a");

julia> x = 2 * a + 1
2*a + 1

julia> coeff(x, 1)
2

julia> x == sum([coeff(x, i - 1) * basis(K)[i] for i in 1:degree(K)]) ==
            sum([coeff(x, i) * a^i for i in 0:degree(K) - 1])
true
```
