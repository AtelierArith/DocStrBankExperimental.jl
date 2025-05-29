```
 EigenModes(Tij::AbstractMatrix{F}) -> ϵ::Vector{Float64}, V::Matrix{F}
```

Numerically diagonalize the hopping matrix `Tij = - V diagm(ϵ) V'` to get the single particle spectrum `ϵ` and the eigenvectors `V`. Note the convention is `H = - \sum_ij Tij c_i^dag c_j` and the decoupled Hamiltonian reads `H = \sum_k ϵ_k f_k^dag f_k` where `c_i = \sum_k V[i,k] f_k`.
