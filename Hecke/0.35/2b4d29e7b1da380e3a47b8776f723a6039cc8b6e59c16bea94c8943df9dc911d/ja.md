```
tensor_product(G::FinGenAbGroup...; task::Symbol = :map) -> FinGenAbGroup, Map
```

与えられた群 $G_i$ に対して、テンソル積 $G_1\otimes \cdots \otimes G_n$ を計算します。`task` が ":map" に設定されている場合、タプル $G_1 \times \cdots \times G_n$ を純テンソル $g_1 \otimes \cdots \otimes g_n$ にマッピングするマップ $\phi$ が返されます。このマップは逆像も持ちます。
