```
iTbd
```

A composite recursive type of supertype `iT` representing a binary phylogenetic tree with  `λ` and `μ` evolving as a Geometric Brownian motion  for `insane` use, with the following fields:

d1:   daughter tree 1   d2:   daughter tree 2   e:    pendant edge   iμ:   if extinct node   fx:   if fix (observed) node   dt:   choice of time lag   fdt:  final `dt`   lλ:   array of a Brownian motion evolution of `log(λ)`   lμ:   array of a Brownian motion evolution of `log(μ)`

iTbd(d1 ::iTbd,           d2 ::iTbd,           e  ::Float64,           dt ::Float64,           fdt::Float64,           iμ ::Bool,           fx ::Bool,           lλ ::Array{Float64,1},           lμ ::Array{Float64,1})
