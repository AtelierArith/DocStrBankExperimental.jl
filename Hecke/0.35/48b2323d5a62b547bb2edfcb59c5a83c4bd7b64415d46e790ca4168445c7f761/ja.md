```
mod(x::AlgAssRelOrdElem, a::AlgAssRelOrdIdl) -> AlgAssRelOrdElem
```

$$
y
$$

を返します `parent(x)` で、$x \equiv y \mod a$ かつ $y$ の係数は $a$ に対して剰余が減少しています。 `parent(x) == order(a)` であり、$a$ が `order(a)` の整数理想であると仮定します。
