```
 (graph,crefs)=graph_monomial_degopt(a; input=:A)
```

[`graph_monomial`](@ref)と同じ多項式を生成しますが、モノミアル基底で生成されます。ただし、これは[`graph_degopt`](@ref)への呼び出しをラップすることによって行われ、`crefs`における自由度が増します。
