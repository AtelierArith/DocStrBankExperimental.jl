```
SSPKnoth
```

`SSPKnoth` is a second-order Rosenbrock method developed by Oswald Knoth.

The coefficients are the same as in `CGDycore.jl`, except that for C we add the diagonal elements too. Note, however, that the elements on the diagonal of C do not really matter because C is only used in its lower triangular part. We add them mostly to match literature on the subject
