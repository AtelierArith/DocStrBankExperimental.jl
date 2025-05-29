```
stevens_matrices(s)
```

Returns the Stevens operators in the spin-`s` representation. The return value `O` can be indexed as `O[k,q]`, where $0 ≤ k ≤ 6$ labels an irrep of SO(3) and $-k ≤ q ≤ k$. This will produce an $N×N$ matrix where $N = 2s + 1$. Linear combinations of Stevens operators can be used as a "physical basis" for decomposing local observables. To see this decomposition, use [`print_stevens_expansion`](@ref).

If `s == Inf`, then symbolic operators will be returned. In this infinite dimensional representation, the Stevens operators become homogeneous polynomials of commuting spin operators.

# Example

```julia
O = stevens_matrices(2)
S = spin_matrices(2)

A = (1/20)O[4,0] + (1/4)O[4,4] + (102/5)I
B = S[1]^4 + S[2]^4 + S[3]^4
@assert A ≈ B
```

See also [`spin_matrices`](@ref) and [Interaction Renormalization](@ref).
