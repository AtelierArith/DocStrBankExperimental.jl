```
compress_haplotypes(reffile::String, tgtfile::String, outfile::String, 
    [d::Int], [minwidth::Int], [overlap::Float64])
```

Cuts a haplotype matrix `reffile` into windows of variable width so that each window has less than `d` unique haplotypes. Saves result to `outfile` as a compressed binary format. All SNPs in `tgtfile` must be present in `reffile`.  All genotypes in `reffile` must be phased and non-missing, and all genotype positions must be unique. 

# Inputs

  * `reffile`: reference haplotype file name (ends in `.vcf`, `.vcf.gz`, or `.bgen`)
  * `tgtfile`: VCF, PLINK, or BGEN file. VCF files should end in `.vcf` or `.vcf.gz`.   PLINK files should exclude `.bim/.bed/.fam` suffixes but the trio must all   be present in the same directory. BGEN files should end in `.bgen`.
  * `outfile`: Output file name (ends in `.jlso`)

# Optional Inputs

  * `d`: Max number of unique haplotypes per genotype window (default `d = 1000`).
  * `minwidth`: Minimum number of typed SNPs per window (default 0)
  * `overlap`: How much overlap between adjacent genotype windows in percentage of   each window's width (default 0.0)

# Why is `tgtfile` required?

The unique haplotypes in each window is computed on the typed SNPs only.  A genotype matrix `tgtfile` is used to identify the typed SNPs. In the future,  hopefully we can pre-compute compressed haplotype panels for all genotyping  platforms and provide them as downloadable files. But currently, users must run this function by themselves. 
