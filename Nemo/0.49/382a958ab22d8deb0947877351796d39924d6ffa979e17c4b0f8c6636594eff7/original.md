```
representation_matrix_q(a::AbsSimpleNumFieldElem)
```

Return a matrix  representing multiplication with $a$ with respect to the power basis of the generator of the parent of $a$. The matrix is returned as a tuple (ZZMatrix, ZZRingElem), consisting of the a primitive integer matrix and a denominator.
