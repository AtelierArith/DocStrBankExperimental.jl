```
evolutionOperatorA(H_lambda, S, Sinv, t)
```

Get evolution operator as Array using the definition

$U(t) = S e^{-i H_\lambda t / \hbar} S^{-1},$

where $\hbar = 1$, $H_{\lambda,ii} = \lambda_i$ are eigenvalues of $H$, so $H$ has to be non-singular, otherwise $H_{\lambda,ij} = 0, i \neq j$.  $S$ is obtained from eigendecomposition of $H$, for example

```julia
H_lambda, S = eigen(Hamiltonian.data)
Sinv = inv(S)
H_lambda = diagm(H_lambda)
```

and arguments have to be Arrays.
