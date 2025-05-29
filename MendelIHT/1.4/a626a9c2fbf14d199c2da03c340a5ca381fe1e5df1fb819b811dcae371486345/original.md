```
simulate_correlated_snparray(s, n, p; block_length, hap, prob)
```

Simulates a SnpArray with correlation. SNPs are divided into blocks where each adjacent SNP is the same with probability prob. There are no correlation between blocks.

# Arguments:

  * `n`: number of samples
  * `p`: number of SNPs
  * `s`: name of SnpArray that will be created (memory mapped) in the current directory. To not memory map, use `undef`.

# Optional arguments:

  * `block_length`: length of each LD block
  * `hap`: number of haplotypes to simulate for each block
  * `prob`: with probability `prob` an adjacent SNP would be the same.
