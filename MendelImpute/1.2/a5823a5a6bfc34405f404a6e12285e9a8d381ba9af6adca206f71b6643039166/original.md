```
phase(tgtfile::String, reffile::String, outfile::String; [impute::Bool],
    [phase::Bool], [dosage::Bool], [rescreen::Bool], [max_haplotypes::Int], 
    [stepwise::Int], [thinning_factor::Int], [scale_allelefreq::Bool], 
    [dynamic_programming::Bool])
```

Main function of MendelImpute program. Phasing (haplotying) of `tgtfile` from a pool of haplotypes `reffile` by sliding windows and saves result in `outfile`. All SNPs in `tgtfile` must be present in `reffile`. Per-SNP quality score will be saved in `outfile`, while per-sample imputation score will be saved in a file ending in `sample.error`.

# Input

  * `tgtfile`: VCF, PLINK, or BGEN file. VCF files should end in `.vcf` or `.vcf.gz`.   PLINK files should exclude `.bim/.bed/.fam` trailings but the trio must all   be present in the same directory. BGEN files should end in `.bgen`
  * `reffile`: Reference haplotype file ending in `.jlso` (compressed binary files).   See [`compress_haplotypes`](@ref)
  * `outfile`: output filename ending in `.vcf.gz`, `.vcf`, or `.jlso`. VCF output   genotypes will have no missing data. If ending in `.jlso`, will output   ultra-compressed data structure recording `HaplotypeMosaicPair`s for    each sample.

# Optional Inputs

  * `impute`: If `true`, imputes every SNPs in `reffile` to `tgtfile`. Otherwise   only missing snps in `tgtfile` will be imputed.
  * `phase`: If `true`, all output genotypes will be phased, but observed data    (minor allele count) may be changed. If `phase=false` all output genotypes   will be unphased but observed minor allele count will not change.
  * `dosage`: If `true`, will assume target matrix are dosages for imputation. Note   this means the genotype matrix will be entirely single precision.
  * `rescreen`: This option is more computationally intensive but gives more   accurate results. It saves a number of top haplotype pairs when solving   the least squares objective, and re-minimize least squares on just   observed data.
  * `max_haplotypes`: Maximum number of haplotypes for using global search. Windows   exceeding this number of unique haplotypes will be searched using a   heuristic. A non-zero `stepscreen` or `thinning_factor` need to be specified
  * `stepwise`: If an integer is specified, will solve the least squares objective   by first finding `stepwise` top haplotypes using a stepwise heuristic then   finds the next haplotype using global search. Uses `max_haplotypes`.
  * `thinning_factor`: If an integer is specified, will solve the least squares   objective on only `thining_factor` unique haplotypes. Uses `max_haplotypes`.
  * `scale_allelefreq`: Boolean indicating whether to give rare SNPs more weight   scaled by `wᵢ = 1 / √2p(1-p)` where max weight is 2.
  * `dynamic_programming`: Boolean indicating whether to phase with a global    search that finds the longest haplotype stretch over all windows. (Currently   broken, sorry!)
