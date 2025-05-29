```
tensor_product(G::FinGenAbGroup...; task::Symbol = :map) -> FinGenAbGroup, Map
```

Given groups $G_i$, compute the tensor product $G_1\otimes \cdots \otimes G_n$. If `task` is set to ":map", a map $\phi$ is returned that maps tuples in $G_1 \times \cdots \times G_n$ to pure tensors $g_1 \otimes \cdots \otimes g_n$. The map admits a preimage as well.
