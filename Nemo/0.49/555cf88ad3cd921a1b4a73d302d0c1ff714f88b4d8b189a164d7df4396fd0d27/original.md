```
gen(L::FqField)
```

Return a $K$-algebra generator `a` of the finite field $L$, where $K$ is the base field of $L$. The element `a` satisfies `defining_polyomial(a) == 0`.

Note that this is in general not a multiplicative generator and can be zero, if $L/K$ is an extension of degree one.
