```
locally_free_basis(a::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> AlgAssAbsOrdElem
```

要素 $x$ を返します。これは $a$ の位数 $O$ のもので、$a_p = O_p \cdot x$ となります。ここで $p$ は $\mathbb Z$ の素数です。`is_locally_free` も参照してください。
