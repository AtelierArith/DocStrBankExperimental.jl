`alpha, c = forward(Nt,a,A,y)`

Computes the scaled forward probabilities ($\bar{\alpha}$) of an Hidden Markov Model (HMM) of `Ns` states with transition matrix `A` (must be a `Ns` × `Ns` matrix), initial probabilities `a` (must be a `Ns`-long vector) and observation likelihoods `y` (must be of size `Nt2` × `Ns` with `Nt2` ≥ `Nt`).

Returns:

  * `alpha` a matrix of size `(Nt,Ns)` containing the forward probabilities
  * `c` a `Nt`-long vector containing the normalization coefficients which can be used to compute the backward probabilities (see `backward`) and the log maximum likelihood (`sum(log.(c))`).

`alpha, c = forward(Nt,t2tr,A,y)`

Here `t2tr` can be an `Nt-1` vector of `Pair{Vector{D},Vector{D}}`. For example given `Nt=3`:

```julia
t2tr = [[1,1]=>[1,2],[1,2]=>[3,3],[3]=>[4]]
```

indicates that at time `t=1` transitions from state `1` to `1` and from `1` to `2` are allowed.  At time `t=2` transitions from state `1` to `3` and from `2` to `3` are allowed. At time `t=3` only the transition from state `3` to `4` is allowed. In practice these indices can be used to construct the (possibly sparse) time-dependent transition matrices described in the [theory section](@ref theory).
