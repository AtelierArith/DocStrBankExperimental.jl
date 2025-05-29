```
function inverse_trace_constant(rd::RefElemData)
```

Returns the degree-dependent constant in the inverse trace equality over the reference element (as reported in ["GPU-accelerated dG methods on hybrid meshes"](https://doi.org/10.1016/j.jcp.2016.04.003) by Chan, Wang, Modave, Remacle, Warburton 2016).

Can be used to estimate dependence of maximum stable timestep on degree of approximation.
