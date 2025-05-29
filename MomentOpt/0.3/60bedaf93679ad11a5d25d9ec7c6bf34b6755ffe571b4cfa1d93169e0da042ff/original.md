```
graph(vref::GMPVariable, indep_vars::Vector{MP.AbstractVariable})

Tries to extract the graph of a scalar function f such that [indep_vars, f(indep_vars)] is the support of vref.
```
