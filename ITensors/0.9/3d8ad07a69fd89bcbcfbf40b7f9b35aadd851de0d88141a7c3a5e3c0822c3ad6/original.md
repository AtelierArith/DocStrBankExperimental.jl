```
flux(inds::Indices, I::Integer...)
```

Get the flux of the block that the specified index falls in.

```
i = Index(QN(0)=>2, QN(1)=>2)
is = (i, dag(i'))
flux(is, 3, 1) == QN(1)
flux(is, 1, 2) == QN(0)
```
