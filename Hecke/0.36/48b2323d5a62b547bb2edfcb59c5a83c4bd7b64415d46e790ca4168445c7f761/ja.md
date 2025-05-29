```
mod(x::AlgAssRelOrdElem, a::AlgAssRelOrdIdl) -> AlgAssRelOrdElem
```

$$
y
$$

を`parent(x)`内で返し、$x \equiv y \mod a$となり、$y$の係数は$a$で剰余が取られます。`parent(x) == order(a)`であり、$a$が`order(a)`の整数理想であると仮定します。
