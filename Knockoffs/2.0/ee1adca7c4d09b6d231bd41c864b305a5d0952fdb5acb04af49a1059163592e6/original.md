```
forward_backward_sampling!(Z, X, Q, q, θ, ...)
```

Samples Z, the hidden states of a HMM, from observed sequence of unphased genotypes X.

# Inputs

`Z`: Length `p` vector of integers. This will store the sampled Markov states `X`: Length `p` vector of genotypes (0, 1, or 2) `Q`: `K × K × p` array. `Q[:, :, j]` is a `K × K` matrix of transition     probabilities for `j`th state, i.e. Q[l, k, j] = P(X*{j} = k | X*{j - 1} = l).     The first transition matrix is not used.  `q`: Length `K` vector of initial probabilities `θ`: The θ parameter estimated from fastPHASE

# Preallocated storage variables

`table`: a `MarkovChainTable` that maps markov chain states to haplotype      pairs (ka, kb) `d`: Sampling distribution, probabilities in d.p are mutated `α̂`: `p × K` scaled forward probability matrix, where      `α̂[j, k] = P(x_1,...,x_k, z_k) / P(x_1,...,x_k)` `c`: normalizing constants, `c[k] = p(x_k | x_1,...,x_{k-1})`

# Reference

Algorithm 3 of "Gene hunting with hidden Markov model knockoffs" by Sesia et al
