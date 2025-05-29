```
entropy_vn(rho)
```

Von Neumann entropy of a density matrix.

The Von Neumann entropy of a density operator is defined as

$$
S(ρ) = -Tr(ρ \log(ρ)) = -\sum_n λ_n\log(λ_n)
$$

where $λ_n$ are the eigenvalues of the density matrix $ρ$, $\log$ is the natural logarithm and $0\log(0) ≡ 0$.

# Arguments

  * `rho`: Density operator of which to calculate Von Neumann entropy.
  * `tol=1e-15`: Tolerance for rounding errors in the computed eigenvalues.
