```
ProductManifold{𝔽,TM<:Tuple} <: AbstractManifold{𝔽}
```

Product manifold $M_1 × M_2 × …  × M_n$ with product geometry.

# Constructor

```
ProductManifold(M_1, M_2, ..., M_n)
```

generates the product manifold $M_1 × M_2 × … × M_n$. Alternatively, the same manifold can be contructed using the `×` operator: `M_1 × M_2 × M_3`.
