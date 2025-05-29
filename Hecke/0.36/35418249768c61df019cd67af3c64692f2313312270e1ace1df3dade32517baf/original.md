```
multiplication_table(A::MatAlgebra; copy::Bool = true) -> Array{RingElem, 3}
```

Given an algebra $A$ this function returns the multiplication table of $A$: If the function returns $M$ and the basis of $A$ is $e_1,\dots, e_n$ then it holds $e_i \cdot e_j = \sum_k M[i, j, k] \cdot e_k$.
