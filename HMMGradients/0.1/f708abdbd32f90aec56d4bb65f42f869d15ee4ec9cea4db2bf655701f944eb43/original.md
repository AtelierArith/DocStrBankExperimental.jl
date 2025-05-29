`backward(Nt,A,c,y)`

Computes the scaled backward probabilities ($\bar{\beta}$) of an Hidden Markov Model (HMM) of `Ns` states with transition matrix `A` (must be a `Ns` × `Ns` matrix), scale coefficients `c` (must be a `Nt`-long vector which is produced by [`forward`](@ref)) and observation likelihoods `y` (must be of size `Nt2` × `Ns` with `Nt2` ≥ `Nt`).
