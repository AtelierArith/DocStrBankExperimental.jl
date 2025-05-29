```
rref_rational(M::MatrixElem{T}) where {T <: RingElement}
```

Return a tuple $(r, A, d)$ consisting of the rank $r$ of $M$ and a denominator $d$ in the base ring of $M$ and a matrix $A$ such that $A/d$ is the reduced row echelon form of $M$. Note that the denominator is not usually minimal.
