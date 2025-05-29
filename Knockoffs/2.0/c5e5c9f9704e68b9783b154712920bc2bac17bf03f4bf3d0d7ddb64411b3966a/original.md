```
get_genotype_transition_matrix(r, θ, α, q, table)
```

Compute transition matrices for the hidden Markov chains in unphased genotypes.  This is equation 9 of "Gene hunting with hidden Markov model knockoffs" by Sesia et al.

# Inputs

`r`: Length `p` vector, the "recombination rates" `θ`: Size `p × K` matrix, `θ[j, k]` is probability that the allele is 1 for SNP `p` at `k`th haplotype motif `α`: Size `p × K` matrix, probabilities that haplotype motifs succeed each other. Rows should sum to 1.  `q`: Length `K` vector of initial probabilities `table`: a `MarkovChainTable` that maps markov chain states k = 1, ..., K+(K+1)/2     to haplotype pairs (ka, kb). 
