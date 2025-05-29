```
IsOrdered <: SemiringProperty
```

Ordered property of a semiring. A semiring is *ordered* if:

1. $a + c ≤ b + c$, $∀ a,b,c ∈ R$ and $a ≤ b$
2. $ac ≤ bc$ and $ca ≤ cb$, $∀ a, b, c ∈ R$, $0 ≤ c$ and $a ≤ b$
