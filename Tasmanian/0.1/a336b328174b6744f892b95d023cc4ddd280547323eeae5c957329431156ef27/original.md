```
makeLocalPolynomialGrid!(tsg::TasmanianSG; order=1, rule="localp", level_limits=Vector{Int32}(undef, 0))
```

creates a new sparse grid using a local polynomial rule discards any existing grid held by TSG

order: int (must be -1 or bigger)         -1 indicates largest possible order          1 means linear, 2 means quadratic, etc.          0 means piece-wise constant, it has different hierarchy            then the other orders, most notably the 1D rule            triples the number of points per level (as opposed            to double for the other cases)

rule: string (defines the 1-D rule that induces the grid)       `localp` `localp-zero`  `semi-localp`  `localp-boundary`
