```
spin_matrices(s)
```

Returns a triple of $N×N$ spin matrices, where $N = 2s+1$. These are the generators of SU(2) in the spin-`s` representation.

If `s == Inf`, then the return values are abstract symbols denoting infinite-dimensional matrices that commute. These can be useful for repeating historical studies, or modeling micromagnetic systems. A technical discussion appears in the Sunny documentation page: [Interaction Renormalization](@ref).

# Example

```julia
S = spin_matrices(3/2)
@assert S'*S ≈ (3/2)*(3/2+1)*I
@assert S[1]*S[2] - S[2]*S[1] ≈ im*S[3]

S = spin_matrices(Inf)
@assert S[1]*S[2] - S[2]*S[1] == 0
```

See also [`print_stevens_expansion`](@ref).
