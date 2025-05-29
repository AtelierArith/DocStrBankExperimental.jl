```
 (graph,crefs)=graph_ps_degopt(a; input=:A)
```

[`graph_ps`](@ref)と同じ多項式を生成します。すなわち、単項式基底係数を持つパターソン–ストックマイヤー手法のグラフです。しかし、これは[`graph_degopt`](@ref)への呼び出しをラップすることによって行われ、`crefs`における自由度が増します。
