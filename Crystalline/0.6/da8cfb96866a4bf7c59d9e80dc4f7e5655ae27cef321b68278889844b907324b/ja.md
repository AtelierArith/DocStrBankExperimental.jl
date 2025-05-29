```
compose(op::SymOperation, rv::RVec)  -->  RVec
```

`op` $= \{\mathbf{W}|\mathbf{w}\}$ と実空間ベクトル `rv` $= \mathbf{r}$ の合成を返します。

この操作は直接作用し、次のように返されます。

$$
    \mathbf{r}' = \{\mathbf{W}|\mathbf{w}\}\mathbf{r} = \mathbf{W}\mathbf{r} + \mathbf{w}.
$$

対応する逆作用 $\{\mathbf{W}|\mathbf{w}\}^{-1}\mathbf{r} =  \mathbf{W}^{-1}\mathbf{r} - \mathbf{W}^{-1}\mathbf{w}$ は `compose(inv(op), rv)` を通じて得ることができます。
