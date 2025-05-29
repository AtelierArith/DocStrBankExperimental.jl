```
divexact_right(a::NCPolyRingElem{T}, b::T; check::Bool=true) where T <: NCRingElem
```

$$
a = qb
$$

と仮定すると、$q$ を返します。デフォルトでは、除算が正確でない場合は例外が発生します。`check=false` の場合、このテストは省略されます。
