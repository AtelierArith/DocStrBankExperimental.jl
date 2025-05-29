```
rdirichlet(d::Domain) = rdiffbc(d, 0)
```

`d`の右端点におけるディリクレ境界条件。[`ldirichlet`](@ref)および[`rdiffbc`](@ref)も参照してください。
