```
is_locally_free(a::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> Bool, AlgAssRelOrdElem
```

$$
O
$$

の要素$x$を持つタプル`(true, x)`を返します。ここで、$a$が$p$で局所的に自由である場合、$a_p = O_p x$となります。それ以外の場合は`(false, 0)`を返します。$p$は`base_ring(O)`の素イデアルです。`locally_free_basis`も参照してください。
