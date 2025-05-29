```
iTct
```

A composite recursive type of supertype `iT` representing a binary phylogenetic tree with  `λ` evolving as a Geometric Brownian motion and constant `μ` for `insane` use, with the following fields:

d1:   daughter tree 1   d2:   daughter tree 2   e:    edge   iμ:   if extinct node   fx:   if fix (observed) node   dt:   choice of time lag   fdt:  final `dt`   lλ:   array of a Brownian motion evolution of `log(λ)`

iTct(d1 ::iTct,           d2 ::iTct,           e  ::Float64,           dt ::Float64,           fdt::Float64,           iμ ::Bool,           fx ::Bool,           lλ ::Array{Float64,1})
