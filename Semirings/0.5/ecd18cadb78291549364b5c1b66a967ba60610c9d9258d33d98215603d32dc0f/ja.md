```
struct BoolSemiring <: Semiring{Bool}
    val::Bool
end
```

ブール半環: $R = ({true, false}, ∨, ∧, false, true)$。
