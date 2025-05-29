`nlogML(Nt,a,A,y)`

Computes the negative log Maximum Likelihood (ML) normalized by the sequence length ($\log(P(\mathbf{X}))/N_t$) of a Hidden Markov Model (HMM) with `Ns` states, transition matrix `A` (a `Ns` × `Ns` matrix), initial probabilities `a` (`Ns`-vector) and observation probabilities `y` (a `Ns`×`Nt` matrix) for `Nt` observations. All `Array`s must have the same element type.

`nlogML(Nt,t2tr,A,y)`

Returns the negative log Maximum Likelihood (ML) normalized by the sequence length ($\log(P(\mathbf{X}))/N_t$) with a constrained path (see [`forward`](@ref)).
