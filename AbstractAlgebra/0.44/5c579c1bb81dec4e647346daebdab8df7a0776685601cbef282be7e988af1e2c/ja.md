```
divexact_right(a::NCPolyRingElem, b::Union{Integer, Rational, AbstractFloat}; check::Bool=true)
```

$$
a = qb
$$

と仮定すると、$q$ を返します。デフォルトでは、除算が正確でない場合は例外が発生します。`check=false` の場合、このテストは省略されます。
