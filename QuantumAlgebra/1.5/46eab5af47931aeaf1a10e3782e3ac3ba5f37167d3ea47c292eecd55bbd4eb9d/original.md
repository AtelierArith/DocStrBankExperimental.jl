```
Avac(A::QuExpr), vacA(A::QuExpr)
```

Simplify operator by assuming it is applied to the vacuum from the left or right, respectively. To be precise, `Avac(A)` returns $A'$ such that $A'|0⟩ = A|0⟩$, while `vacA(A)` does the same for $⟨0|A$.
