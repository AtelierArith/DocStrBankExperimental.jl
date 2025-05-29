```
L = lyapop(A; disc = false, her = false)
```

Define, for an `n x n` matrix `A`, the continuous Lyapunov operator `L:X -> AX+XA'` if `disc = false` or the discrete Lyapunov operator `L:X -> AXA'-X` if `disc = true`. If `her = false` the Lyapunov operator `L:X -> Y` maps general square matrices `X` into general square matrices `Y`, and the associated matrix `M = Matrix(L)` is $n^2 \times n^2$. If `her = true` the Lyapunov operator `L:X -> Y` maps symmetric/Hermitian matrices `X` into symmetric/Hermitian matrices `Y`, and the associated matrix `M = Matrix(L)` is $n(n+1)/2 \times n(n+1)/2$. For the definitions of the Lyapunov operators see:

M. Konstantinov, V. Mehrmann, P. Petkov. On properties of Sylvester and Lyapunov operators. Linear Algebra and its Applications 312:35–71, 2000.
