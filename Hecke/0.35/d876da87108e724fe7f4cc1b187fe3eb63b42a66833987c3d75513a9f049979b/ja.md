```
is_locally_free(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl, p::ZZRingElem
               side = :right) -> Bool, AlgAssAbsOrdElem
```

$$
O
$$

の要素$x$を持つタプル`(true, x)`を返します。ここで、$a O_p = x O_p$または$O_p a = O_p x$であり、$a$が$p$で右（または左）局所自由イデアルである場合、そうでなければ`(false, 0)`を返します。$a$は$O$のイデアルであり、$a \subseteq O$であると仮定します。

`locally_free_basis`も参照してください。
