```
degree_histogram(g, degfn=degree)
```

キーで表される次数を持つ頂点の数を表す値を持つ`Dict`を返します。

次数関数（例えば、[`indegree`](@ref)や[`outdegree`](@ref)）は、`degfn`をオーバーライドすることで指定できます。
