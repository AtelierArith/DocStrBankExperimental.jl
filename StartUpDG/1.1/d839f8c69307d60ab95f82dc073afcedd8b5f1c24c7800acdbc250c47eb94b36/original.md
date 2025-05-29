```
RefElemData(elem::Union{Tri, Tet, Pyr}, approx_type::Polynomial{<:TensorProductQuadrature}, N; kwargs...)
RefElemData(elem::Union{Wedge}, 
                 approx_type::Polynomial{<:TensorProductQuadrature}, N; 
                 quad_rule_tri = stroud_quad_nodes(Tri(), 2 * N),
                 quad_rule_line = gauss_quad(0, 0, N),
                 kwargs...)
```

Uses collapsed coordinate volume quadrature. Should be called via

```julia
RefElemData(Tri(), Polynomial(TensorProductQuadrature()), N)
```
