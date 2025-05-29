```
is_locally_free(O::AlgAssAbsOrd, a::AlgAssAbsOrdIdl, p::ZZRingElem
               side = :right) -> Bool, AlgAssAbsOrdElem
```

タプル `(true, x)` を返します。ここで、$x$ は $O$ の要素であり、$a O_p = x O_p$ または $O_p a = O_p x$ となるようなもので、$a$ が $p$ において右（または左）局所自由イデアルである場合に返されます。それ以外の場合は `(false, 0)` が返されます。$a$ は $O$ のイデアルであり、$a \subseteq O$ であると仮定されています。

`locally_free_basis` も参照してください。
