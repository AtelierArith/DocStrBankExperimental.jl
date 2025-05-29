```
ldirichlet(d::Domain) = ldiffbc(d, 0)
```

`d`の左端点におけるディリクレ境界条件。[`rdirichlet`](@ref)および[`ldiffbc`](@ref)も参照してください。
