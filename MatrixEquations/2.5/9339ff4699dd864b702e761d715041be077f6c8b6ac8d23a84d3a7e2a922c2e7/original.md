```
X = hlyapckr(A,C, isig = 1; atol::Real=0, rtol::Real=atol>0 ? 0 : N*ϵ)
```

Compute for `isig = ±1` a solution of the continuous H-Lyapunov matrix equation

```
            A*X + isig*adjoint(X)*adjoint(A) + C = 0
```

using the Kronecker product expansion of equations. `A` and `C` are `m×n` and `m×m` matrices, respectively, and `X` is an `n×m` matrix. The matrix `C` must be hermitian if `isig = 1` and skew-hermitian if `isig = -1`. `atol` and `rtol` are the absolute and relative tolerances, respectively, used for rank computation.  The default relative tolerance is `N*ϵ`,   where `N = 4*min(m,n)^2` and ϵ is the machine precision of the element type of `A`. This function is not recommended for large order matrices.
