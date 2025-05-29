```
GBS(totalQTL, totalSNP, muDensity, sigmasqDensity, winSize, muAlleleFreq, sigmasqAlleleFreq, re, meanDepth, barcodeFile, useChr, plotOutput, writeOutput, onlyOutputGBS)
```

Simulate Genotyping-by-Sequencing (GBS) data.

This function generates GBS reads by inserting genomic variants into *in silico* digested genomic fragments, ligates the polymorphic sequence with barcodes and replicates based on sequencing depth.

# Arguments

  * `totalQTL`: total number of QTL to be simulated
  * `totalSNP`: total number of SNPs to be simulated (set to "0" if sampling SNP positions based on density)
  * `muDensity`: location parameter of log-Laplace distribution (for sampling SNP density)
  * `sigmasqDensity`: scale parameter of log-Laplace distribution (for sampling SNP density)
  * `winSize`: Size of window and bin for sampling SNP positions
  * `muAlleleFreq`: mean of sampled allele frequency
  * `sigmasqAlleleFreq`: variance of sampled allele frequency
  * `re`: restriction enzyme(s) to be used
  * `barcodeFile`: file containing GBS barcodes
  * `useChr`: either the number of chromosomes or a set of chromosome(s) to be simulated
  * `plotOutput`: set to true if graphical outputs are required
  * `writeOutput`: set to true if text outputs are required
  * `onlyOutputGBS`: set to true if only GBS data is kept

# Examples

```julia
julia> GBS(100, 0, -2.0, 0.001, 1000000, 0.5, 0.001, [SimGBS.ApeKI], 20.0, "GBS_Barcodes.txt", [1], false, true, true)
```
