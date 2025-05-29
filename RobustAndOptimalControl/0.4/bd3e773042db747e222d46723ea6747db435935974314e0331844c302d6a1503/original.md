```
μ = structured_singular_value(M; tol=1e-4, scalings=false, dynamic=false)
```

Compute (an upper bound of) the structured singular value μ for diagonal Δ of complex perturbations (other structures of Δ are not yet supported). `M` is assumed to be an (n × n × N_freq) array or a matrix.

We currently don't have any methods to compute a lower bound, but if all perturbations are complex the spectral radius `ρ(M)` is always a lower bound (usually not a good one).

If `scalings = true`, return also a `n × nf` matrix `Dm` with the diagonal scalings `D` such that

```
D = Diagonal(Dm[:, i])
σ̄(D\M[:,:,i]*D)
```

is minimized.

If `dynamic = true`, the perturbations are assumed to be time-varying `Δ(t)`. In this case, the same scaling is used for all frequencies and the returned `D` if `scalings=true` is a vector `d` such that `D = Diagonal(d)`.
