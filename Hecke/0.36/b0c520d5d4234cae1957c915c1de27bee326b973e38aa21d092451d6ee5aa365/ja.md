```
integral_split(a::FieldElem, O::Ring)
```

ある環 $O$ の商体の要素に対して、$a$ を環 $O$ の要素 $n$ と、$O$ または $O$ の係数環のいずれかの分母 $d$ に分解します。

# 例

```julia
julia> integral_split(1//3, ZZ)
(1, 3)

julia> k, a = quadratic_field(5);

julia> zk = maximal_order(k);

julia> integral_split(1//a, zk)
(5, [-1 2])
```
