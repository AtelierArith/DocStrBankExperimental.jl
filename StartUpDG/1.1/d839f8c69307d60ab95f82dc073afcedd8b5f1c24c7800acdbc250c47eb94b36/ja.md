```
RefElemData(elem::Union{Tri, Tet, Pyr}, approx_type::Polynomial{<:TensorProductQuadrature}, N; kwargs...)
RefElemData(elem::Union{Wedge}, 
                 approx_type::Polynomial{<:TensorProductQuadrature}, N; 
                 quad_rule_tri = stroud_quad_nodes(Tri(), 2 * N),
                 quad_rule_line = gauss_quad(0, 0, N),
                 kwargs...)
```

縮退座標体積数値積分を使用します。次のように呼び出す必要があります。

```julia
RefElemData(Tri(), Polynomial(TensorProductQuadrature()), N)
```
