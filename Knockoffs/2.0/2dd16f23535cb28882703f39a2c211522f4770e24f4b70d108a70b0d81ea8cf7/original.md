```
get_haplotype_transition_matrix(r, θ, α)
```

Compute transition matrices for the hidden Markov chains in haplotypes.  This is 2 equations above eq8 in "Gene hunting with hidden Markov model knockoffs" by Sesia et al.

# Inputs

`r`: Length `p` vector, the "recombination rates" `θ`: Size `p × K` matrix, `θ[j, k]` is probability that the allele is 1 for SNP `p` at `k`th haplotype motif `α`: Size `p × K` matrix, probabilities that haplotype motifs succeed each other. Rows should sum to 1. 

# Output

`Q`: A `p`-dimensional vector of `K × K` matrices. `Q[:, :, j]` is the `j`th transition matrix. 
