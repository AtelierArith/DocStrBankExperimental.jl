```
LINV = invlyapop(A; disc = false, her = false)
```

Define `LINV`, the inverse of the continuous Lyapunov operator `L:X -> AX+XA'` for `disc = false` or the inverse of the discrete Lyapunov operator `L:X -> AXA'-X` for `disc = true`, where `A` is an `n x n` matrix. If `her = false` the inverse Lyapunov operator `LINV:Y -> X` maps general square matrices `Y` into general square matrices `X`, and the associated matrix `M = Matrix(LINV)` is $n^2 \times n^2$. If `her = true` the inverse Lyapunov operator `LINV:Y -> X` maps symmetric/Hermitian matrices `Y` into symmetric/Hermitian matrices `X`, and the associated matrix `M = Matrix(LINV)` is $n(n+1)/2 \times n(n+1)/2$. For the definitions of the Lyapunov operators see:

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
