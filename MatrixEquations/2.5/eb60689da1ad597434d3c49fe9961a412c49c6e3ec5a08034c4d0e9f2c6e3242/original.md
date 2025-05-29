```
M = sylvop(A, B; disc = false)
```

Define the continuous Sylvester operator `M: X -> AX+XB` if `disc = false` or the discrete Sylvester operator `M: X -> AXB+X` if `disc = true`, where `A` and `B` are square matrices.
