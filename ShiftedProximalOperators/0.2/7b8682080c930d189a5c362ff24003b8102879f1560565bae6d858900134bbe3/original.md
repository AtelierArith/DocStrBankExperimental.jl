```
GroupNormL2(λ = 1, idx = [:])
```

Returns the group $\ell_2$-norm operator

$$
f(x) =  \sum_i \lambda_i \|x_{[i]}\|_2^{1/2}
$$

for groups $x_{[i]}$ and nonnegative weights $\lambda_i$. The group $\ell_2$-norm operator reduces to the $\ell_2$-norm if only one group is defined (the default).
