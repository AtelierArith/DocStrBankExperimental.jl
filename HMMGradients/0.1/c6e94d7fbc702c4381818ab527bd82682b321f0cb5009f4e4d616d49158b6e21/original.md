`logalpha, logML = logforward(Nt,a,A,y)`

Computes the scaled forward log-probabilities ($\hat{\alpha}$) of an Hidden Markov Model (HMM) of `Ns` states with log-transition matrix `A` (must be a `Ns` × `Ns` matrix), initial log-probabilities `a` (must be a `Ns`-long vector) and observation log-likelihoods `y` (must be of size `Nt2` × `Ns` with `Nt2` ≥ `Nt`).

Returns:

  * `logalpha` a matrix of size `(Nt,Ns)` containing the forward log-probabilities
  * `logML` the log likelihood of the observation normalized by the sequence length, i.e. $\log(P(\mathbf{X}))/N_t$.

`logalpha, logML = logforward(Nt,t2tr,A,y)`

Returns the forward log-probabilities with a constrained path (see [`forward`](@ref)).
