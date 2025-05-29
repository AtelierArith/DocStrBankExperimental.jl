```
prime_decomposition(O::AbsNumFieldOrder,
                    p::Integer,
                    degree_limit::Int = 0,
                    lower_limit::Int = 0) -> Vector{Tuple{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}}
```

配列のタプル $(\mathfrak p_i,e_i)$ を返します。ここで、$p \mathcal O$ は $\mathfrak p_i^{e_i}$ の積であり、$i \neq j$ の場合は $\mathfrak p_i \neq \mathfrak p_j$ です。

`degree_limit` が非ゼロの整数 $k > 0$ の場合、$\deg(\mathfrak p) \leq k$ を満たす素イデアル $\mathfrak p$ のみが返されます。同様に、`lower_limit` が非ゼロの整数 $l > 0$ の場合、$l \leq \deg(\mathfrak p)$ を満たす素イデアル $\mathfrak p$ のみが返されます。この場合、$p\mathcal O$ が $\mathfrak p_i^{e_i}$ の積でないことがあることに注意してください。
