`logbackward(Nt,A,y)`

Computes the backward log-probabilities ($\hat{\beta}$) of an Hidden Markov Model (HMM) of `Ns` states with log-transition matrix `A` (must be a `Ns` × `Ns` matrix), scale coefficients and observation log-likelihoods `y` (must be of size `Nt2` × `Ns` with `Nt2` ≥ `Nt`).
