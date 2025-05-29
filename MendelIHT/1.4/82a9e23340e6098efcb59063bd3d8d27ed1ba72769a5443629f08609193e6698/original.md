```
simulate_random_snparray(s::String, n::Integer, p::Integer; 
    [mafs::Vector{Float64}], [min_ma::Integer])
```

Creates a random SnpArray in the current directory without missing value,  where each SNP has ⫺5 (default) minor alleles. 

Note: if supplied minor allele frequency is extremely small, it could take a long time for the simulation to generate samples where at least `min_ma` (defaults to 5) are present. 

# Arguments:

  * `s`: name of SnpArray that will be created in the current directory. To not   create file, use `undef`.
  * `n`: number of samples
  * `p`: number of SNPs

# Optional Arguments:

  * `mafs`: vector of desired minor allele freuqencies (uniform(0,0.5) by default)
  * `min_ma`: the minimum number of minor alleles that must be present for each   SNP (defaults to 5)
