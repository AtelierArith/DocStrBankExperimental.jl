```
LSMR(; krylovdim=1,
        maxiter=KrylovDefaults.maxiter[],
        tol=KrylovDefaults.tol[], 
        orth::Orthogonalizer=ModifiedGramSchmidt(),
        verbosity=KrylovDefaults.verbosity[])
```

Represents the LSMR algorithm, which minimizes $\|Ax - b\|^2 + \|λx\|^2$ in the Euclidean norm. If multiple solutions exists the minimum norm solution is returned. The method is based on the Golub-Kahan bidiagonalization process. It is algebraically equivalent to applying MINRES to the normal equations $(A^*A + λ^2I)x = A^*b$, but has better numerical properties, especially if $A$ is ill-conditioned.

The `LSMR` method will search for the optimal $x$ in a Krylov subspace of maximal size  `maxiter`, or stop when $norm(A'*(A*x - b) + λ^2 * x) < tol$. The parameter `krylovdim` does in this case not indicate that a subspace of that size will be built, but represents the number of most recent vectors that will be kept to which the next vector will be reorthogonalized. The default verbosity level `verbosity` amounts to printing warnings upon lack of convergence.

See also: [`lssolve`](@ref)
