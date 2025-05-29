```
divexact(A::SRow, b::RingElem; check::Bool = true) -> SRow
```

Return $C$ such that $a = b \cdot C$. Calls the function `divexact_left(A,b;check)`
