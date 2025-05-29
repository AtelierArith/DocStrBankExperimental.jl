```julia
applychannel(Φ, ρ)

```

  * `Φ`: list of vectors.
  * `ρ`: input matrix.

Return application of channel `Φ``on`ρ`. Kraus representation of quantum channel $\Phi$ is a set $\{K_i\}_{i\in I}$ of bounded operators on $\mathcal{H}$ such that $\sum_{i\in I} K_i^\dagger K_i = \mathcal{1}$. Then $\Phi(\rho)=\sum_{i\in I} K_i \rho K_i^\dagger$.
