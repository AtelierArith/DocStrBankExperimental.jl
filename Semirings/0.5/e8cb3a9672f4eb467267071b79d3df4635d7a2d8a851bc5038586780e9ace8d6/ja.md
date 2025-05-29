```
IsOrdered <: SemiringProperty
```

半環の順序付けプロパティ。半環は*順序付けられている*場合、次の条件を満たします：

1. $$
    a + c ≤ b + c
    $$

    , $∀ a,b,c ∈ R$ および $a ≤ b$
2. $$
    ac ≤ bc
    $$

    および $ca ≤ cb$, $∀ a, b, c ∈ R$, $0 ≤ c$ および $a ≤ b$
