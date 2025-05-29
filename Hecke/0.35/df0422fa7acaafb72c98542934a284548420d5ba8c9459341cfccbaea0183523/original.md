```
fixed_field(K::SimpleNumField,
            sigma::Map;
            simplify::Bool = true) -> number_field, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

Given a number field $K$ and an automorphism $\sigma$ of $K$, this function returns the fixed field of $\sigma$ as a pair $(L, i)$ consisting of a number field $L$ and an embedding of $L$ into $K$.

By default, the function tries to find a small defining polynomial of $L$. This can be disabled by setting `simplify = false`.
