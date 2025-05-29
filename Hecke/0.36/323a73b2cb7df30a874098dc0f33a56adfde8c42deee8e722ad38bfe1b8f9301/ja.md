```
locally_free_basis(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl,
                   p::Union{ Int, ZZRingElem }) -> AlgAssAbsOrdElem
```

$$
O
$$

の要素$x$を返します。ここで、$a_p = O_p \cdot x$であり、$p$は$\mathbb Z$の素数です。$a$は$O$の理想であり、$a \subseteq O$であると仮定します。`is_locally_free`も参照してください。
