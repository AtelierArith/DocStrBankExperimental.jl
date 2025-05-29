```
ArnoldiWorkspace(n, k) → ArnoldiWorkspace
ArnoldiWorkspace(v1, k) → ArnoldiWorkspace
ArnoldiWorkspace(V, H; V_tmp, Q) → ArnoldiWorkspace
```

Holds the large arrays for the Arnoldi relation: Vₖ₊₁ and Hₖ are matrices that satisfy A * Vₖ = Vₖ₊₁ * Hₖ, where Vₖ₊₁ is orthonormal of size n × (k+1) and Hₖ upper  Hessenberg of size (k+1) × k. The matrices V_tmp and Q are used for restarts, and have similar size as Vₖ₊₁ and Hₖ (but Q is k × k, not k+1 × k).

## Examples

```julia
# allocates workspace for 20-dimensional Krylov subspace
arnoldi = ArnoldiWorkspace(100, 20)

# allocate workspace for 20-dimensional Krylov subspace, with initial vector ones(100) copied into
# the first column of V
arnoldi = ArnoldiWorkspace(ones(100), 20)

# manually allocate workspace with V, H
V = Matrix{Float64}(undef, 100, 21)
H = Matrix{Float64}(undef, 21, 20)
arnoldi = ArnoldiWorkspace(V, H)

# manually allocate all arrays, including temporaries
V, tmp = Matrix{Float64}(undef, 100, 21), Matrix{Float64}(undef, 100, 21)
H, Q = Matrix{Float64}(undef, 21, 20), Matrix{Float64}(undef, 20, 20)
arnoldi = ArnoldiWorkspace(V, H, V_tmp = tmp, Q = Q)
```
