```
localization(K::RationalFunctionField{T}, ::typeof(degree)) where T <: FieldElement
```

$$
k[1/x]
$$

の$(1/x)$における局所化を、すなわち有理関数体$k(x)$における無限遠点での局所化、すなわち評価$-$degree$(x)$に対する評価環を返します。これはリング$k_\infty(x) = \{ f/g | \deg(f) \leq \deg(g)\}$です。
