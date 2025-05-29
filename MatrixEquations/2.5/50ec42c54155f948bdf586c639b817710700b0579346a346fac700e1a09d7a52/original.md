```
LINV = invlyapop(A, E; disc = false, her = false)
```

Define `LINV`, the inverse of the continuous Lyapunov operator `L:X -> AXE'+EXA'` for `disc = false` or the inverse of the discrete Lyapunov operator `L:X -> AXA'-EXE'` for `disc = true`, where `(A,E)` is a pair of `n x n` matrices. If `her = false` the inverse Lyapunov operator `LINV:Y -> X` maps general square matrices `Y` into general square matrices `X`, and the associated matrix `M = Matrix(LINV)` is $n^2 \times n^2$. If `her = true` the inverse Lyapunov operator `LINV:Y -> X` maps symmetric/Hermitian matrices `Y` into symmetric/Hermitian matrices `X`, and the associated matrix `M = Matrix(LINV)` is $n(n+1)/2 \times n(n+1)/2$. For the definitions of the Lyapunov operators see:

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
