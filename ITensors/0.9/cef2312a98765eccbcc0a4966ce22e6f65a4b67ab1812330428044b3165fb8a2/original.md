```
flux(inds::Indices, block::Tuple{Vararg{Int}})
```

Get the flux of the specified block, for example:

```
i = Index(QN(0)=>2, QN(1)=>2)
is = (i, dag(i'))
flux(is, Block(1, 1)) == QN(0)
flux(is, Block(2, 1)) == QN(1)
flux(is, Block(1, 2)) == QN(-1)
flux(is, Block(2, 2)) == QN(0)
```
