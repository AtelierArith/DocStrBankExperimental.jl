```
reduce_full(A::SMat{ZZRingElem}, g::SRow{ZZRingElem},
                      with_transform = Val(false)) -> SRow{ZZRingElem}, Vector{Int}
```

Reduces $g$ modulo $A$ and assumes that $A$ is upper triangular.

The second return value is the array of pivot elements of $A$ that changed.

If `with_transform` is set to `Val(true)`, then additionally an array of transformations is returned.
