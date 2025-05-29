```
locally_free_basis(O::AlgAssRelOrd, a::AlgAssRelOrdIdl,
                   p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal }) -> AlgAssRelOrdElem
```

$$
O
$$

の要素$x$を返します。ここで、$a_p = O_p \cdot x$であり、$p$は`base_ring(O)`の素イデアルです。$a$は$O$のイデアルであり、$a \subseteq O$であると仮定されています。`is_locally_free`も参照してください。
