```
inv(x::ComplexMatrix)
```

Given a $n\times n$ matrix of type `AcbMatrix`, return an $n\times n$ matrix $X$ such that $AX$ contains the identity matrix. If $A$ cannot be inverted numerically an exception is raised.
