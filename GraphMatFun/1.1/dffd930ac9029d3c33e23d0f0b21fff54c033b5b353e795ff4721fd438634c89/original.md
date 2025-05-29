```
 (graph,crefs)=graph_monomial(a; input=:A, polyname=:P)
```

Generates the graph for the polynomial using the monomial basis coefficients. More precisely, it corresponds to the evaluation of the polynomial

```
p(s) = a[1] + a[2]*s + ... + a[n]*s^(n-1),
```

where s^k is naively evaluated as s^k=s*s^(k-1) for k=2,3,...,n-1. The kwarg `polyname` specifies the name of intermediate variables.
