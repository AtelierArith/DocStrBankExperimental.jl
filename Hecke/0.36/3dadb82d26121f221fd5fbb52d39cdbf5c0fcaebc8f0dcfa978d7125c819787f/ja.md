```
hom(G::FinGenAbGroup, H::FinGenAbGroup; task::Symbol = :map) -> FinGenAbGroup, Map
```

$$
G
$$

から $H$ へのすべての準同型の群を抽象群として計算します。`task` が ":map" の場合、実際の準同型を取得するために使用できるマップ $\phi$ が計算されます。このマップは逆像も許可します。マップを計算しないようにするには、`task` を ":none" に設定してください。
