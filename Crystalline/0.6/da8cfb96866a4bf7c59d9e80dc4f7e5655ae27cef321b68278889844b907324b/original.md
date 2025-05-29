```
compose(op::SymOperation, rv::RVec)  -->  RVec
```

Return the composition of `op` $= \{\mathbf{W}|\mathbf{w}\}$ and a real-space vector `rv` $= \mathbf{r}$.

The operation is taken to act directly, returning

$$
    \mathbf{r}' = \{\mathbf{W}|\mathbf{w}\}\mathbf{r} = \mathbf{W}\mathbf{r} + \mathbf{w}.
$$

The corresponding inverse action $\{\mathbf{W}|\mathbf{w}\}^{-1}\mathbf{r} =  \mathbf{W}^{-1}\mathbf{r} - \mathbf{W}^{-1}\mathbf{w}$ can be obtained via  `compose(inv(op), rv)`.
