```
descendencematrix(net::HybridNetwork; checkpreorder::Bool=true)
```

ネットワークのすべてのノード間の子孫行列: オブジェクト `D` は [`MatrixTopologicalOrder`](@ref) 型であり、`D[i,j]` はノード `i` における遺伝物質のうちノード `j` に遡ることができる割合です。もし `D[i,j]>0` であれば、`j` は `i` の子孫であり（`j` は `i` の先祖でもあります）。`checkpreorder` が false の場合、ネットワークは事前順序付けされていると仮定されます。`checkpreorder` が true（デフォルト）の場合、事前順序付けがネットワークに対して事前に実行されます。
