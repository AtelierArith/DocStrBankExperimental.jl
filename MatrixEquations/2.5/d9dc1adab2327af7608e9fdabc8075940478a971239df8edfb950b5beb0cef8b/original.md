```
X = tlyapc(A,C, isig = 1; fast = true, atol::Real=0, rtol::Real=atol>0 ? 0 : N*ϵ)
```

Compute for `isig = ±1` a solution of the continuous T-Lyapunov matrix equation

```
            A*X + isig*transpose(X)*transpose(A) + C = 0
```

using explicit formulas based on full rank factorizations of `A`  (see [1] and [2]).  `A` and `C` are `m×n` and `m×m` matrices, respectively, and `X` is an `n×m` matrix. The matrix `C` must be symmetric if `isig = 1` and skew-symmetric if `isig = -1`. `atol` and `rtol` are the absolute and relative tolerances, respectively, used for rank computation.  The default relative tolerance is `N*ϵ`, where `N = min(m,n)` and ϵ is the machine precision of  the element type of `A`.

The underlying rank revealing factorization of `A` is the QR-factorization with column pivoting,  if `fast = true` (default), or the more reliable SVD-decomposition, if `fast = false`.

[1] H. W. Braden. The equations A^T X ± X^T A = B. SIAM J. Matrix Anal. Appl., 20(2):295–302, 1998.

[2] C.-Y. Chiang, E. K.-W. Chu, W.-W. Lin, On the ★-Sylvester equation AX ± X^★ B^★ = C.     Applied Mathematics and Computation, 218:8393–8407, 2012.
