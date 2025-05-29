```
 (graph,crefs)=graph_newton_schulz_degopt(k, T=ComplexF64; input=:A)
```

これは、再帰を使用して逆数を近似するためのニュートン–シュルツ反復の `k` 回の反復を行います。

```
Z_i=A*V_i
V_{i+1}=V_i*(2*I-Z_i).
```

この関数は [`graph_degopt`](@ref) を呼び出し、`crefs` における自由度を増加させます。さらに [`graph_newton_schulz`](@ref) も参照してください。
