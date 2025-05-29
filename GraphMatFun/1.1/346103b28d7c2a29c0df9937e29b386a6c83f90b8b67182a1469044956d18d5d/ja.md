```
 (graph, cref) = graph_rational(den_coeffs, num_coeffs, poly_gen=graph_ps)
 (graph, cref) = graph_rational(
    den_graph,
    num_graph;
    den_cref = Vector{Tuple{Symbol,Int}}(),
    num_cref = Vector{Tuple{Symbol,Int}}(),
)
```

有理近似のグラフを生成します

```
r(A)=q(A)^{-1}p(A)
```

ここで、p(A) と q(A) は係数 `den_coeffs` と `num_coeffs` によって定義され、関数 `poly_gen` によって生成されます。この関数は `(graph,cref)=poly_gen(coeffs)` のように呼び出されます。例えば、[`graph_monomial`](@ref) や [`graph_ps`](@ref) を参照してください。

代替の呼び出しシグネチャは、p と q のグラフを直接使用し、`den_graph` と `num_graph` として指定します。対応する `den_cref` と `num_cref` も渡すことができ、適宜修正されます。そうでない場合、この呼び出しの戻り値 `cref` は空になります。
