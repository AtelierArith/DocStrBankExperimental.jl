```
metasymbols(md::MatrixDescriptor)
```

Return a vector of symbols, which point to metadata of the problem. These symbols `s` may be used to access the objects by `getproperty(md, s)` or by `getindex(md, s)`. The syntax `md.S` is preferred, if `S` is a constant `Julia` word. In any case `md[s]` is possible.

Example: `md = mdopen("*/bfly"); A = md.A; co = md.coord; txt10 = md["Gname_10.txt"]`
