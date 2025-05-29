```
struct BoolSemiring <: Semiring{Bool}
    val::Bool
end
```

Boolean semiring: $R = ({true, false}, ∨, ∧, false, true)$.
