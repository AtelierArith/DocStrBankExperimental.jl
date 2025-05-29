```
sTxs
```

A composite recursive type of supertype `Tx` representing a binary phylogenetic tree with traits `xv` and their rates `lσ2` with the following fields:

d1:   daughter tree 1   d2:   daughter tree 2   e:    edge   dt:   choice of time lag   fdt:  final `dt`   xv:   array of a Brownian motion evolution of `X`.   lσ2:  array of a Brownian motion evolution of `log(σ)`.

sTxs(d1 ::sTxs,        d2 ::sTxs,        e  ::Float64,        dt ::Float64,        fdt::Float64,        xv ::Array{Float64,1},        lσ2 ::Array{Float64,1})
