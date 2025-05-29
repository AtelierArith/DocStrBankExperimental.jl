```
divexact_right(f::NCPolyRingElem{T}, g::NCPolyRingElem{T}; check::Bool=true) where T <: NCRingElem
```

$$
f = qg
$$

と仮定すると、$q$ を返します。デフォルトでは、除算が正確でない場合は例外が発生します。`check=false` の場合、このテストは省略されます。
