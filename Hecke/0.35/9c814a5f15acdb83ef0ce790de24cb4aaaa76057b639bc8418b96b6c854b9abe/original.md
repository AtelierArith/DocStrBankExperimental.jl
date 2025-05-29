```
multiplication_table(A::GroupAlgebra; copy::Bool = true) -> Matrix{RingElem}
```

Given a group algebra $A$ this function returns the multiplication table of $A$: If the function returns $M$ and the basis of $A$ is $g_1,\dots, g_n$ then it holds $g_i \cdot g_j = g_{M[i, j]}$.
