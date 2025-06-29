```
 (graph, cref) = graph_rational(den_coeffs, num_coeffs, poly_gen=graph_ps)
 (graph, cref) = graph_rational(
    den_graph,
    num_graph;
    den_cref = Vector{Tuple{Symbol,Int}}(),
    num_cref = Vector{Tuple{Symbol,Int}}(),
)
```

Generates the graph for the rational approximation

```
r(A)=q(A)^{-1}p(A)
```

where p(A) and q(A) are polynomials defined by the coefficients `den_coeffs` and `num_coeffs`, and generated by the function `poly_gen`, which is called as `(graph,cref)=poly_gen(coeffs)`, see, e.g., [`graph_monomial`](@ref) and [`graph_ps`](@ref).

The alternative call-signature involves the graphs for p and q directly, as `den_graph` and `num_graph`. The corresponding `den_cref` and `num_cref` can also be passed to be modified accordingly, otherwise the return value `cref` is empty for this call.
