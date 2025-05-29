```
locally_free_basis(a::AlgAssRelOrdIdl, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> AlgAssRelOrdElem
```

要素 $x$ を返します。これは $a$ の順序 $O$ のもので、$a_p = O_p \cdot x$ となります。ここで、$p$ は `base_ring(O)` の素イデアルです。`is_locally_free` も参照してください。
