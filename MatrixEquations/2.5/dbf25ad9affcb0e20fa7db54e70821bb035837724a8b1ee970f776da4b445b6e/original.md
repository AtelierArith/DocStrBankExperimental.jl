```
X = hsylvckr(A,B,C; atol::Real=0, rtol::Real=atol>0 ? 0 : N*ϵ)
```

Compute a solution of the continuous H-Sylvester matrix equation

```
            A*X + adjoint(X)*B = C
```

using the Kronecker product expansion of equations. `A`, `B` and `C` are `m×n`, `n×m` and `m×m` matrices, respectively, and `X` is an `n×m` matrix. `atol` and `rtol` are the absolute and relative tolerances, respectively, used for rank computation.  The default relative tolerance is `N*ϵ`,   where `N = 4*min(m,n)^2` and ϵ is the machine precision of the element type of `A`. This function is not recommended for large order matrices.
