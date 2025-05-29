```
norm(psum::PauliSum, L=2)
```

Calculate the norm of a `PauliSum` with respect to the `L`-norm.  Calls LinearAlgebra.norm on the coefficients of the `PauliSum`.
