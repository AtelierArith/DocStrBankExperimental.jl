```
MINV = invsylvop(A, B; disc = false)
```

Define `MINV`, the inverse of the continuous Sylvester operator  `M: X -> AX+XB` if `disc = false` or of the discrete Sylvester operator `M: X -> AXB+X` if `disc = true`, where `A` and `B` are square matrices.
