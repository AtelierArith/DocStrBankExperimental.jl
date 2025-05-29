```
is_locally_free(a::AlgAssAbsOrdIdl, p::Union{ Int, ZZRingElem })
  -> Bool, AlgAssAbsOrdElem
```

$ a $が $ p $ で局所的に自由である場合、$ a*p = O*p x $ となる $ a $ の順序 $ O $ の要素 $ x $ を持つタプル $(true, x)$ を返し、そうでない場合は $(false, 0)$ を返します。 $ p $ は $\mathbb Z$ の素数です。`locally_free_basis` も参照してください。
