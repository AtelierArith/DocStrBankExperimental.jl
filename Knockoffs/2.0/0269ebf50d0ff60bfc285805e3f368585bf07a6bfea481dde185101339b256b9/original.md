```
rapid(rapid_exe, vcffile, mapfile, d, outfolder, w, r, s, [a])
```

Wrapper for the RaPID program. 

# Inputs

  * `rapid_exe`: Full path to the `RaPID_v.1.7` executable file
  * `vcffile`: Phased VCF file name
  * `mapfile`: Map file name
  * `d`: Actual Minimum IBD length in cM
  * `outfolder`: Output folder name
  * `w`: Number of SNPs in a window for sub-sampling
  * `r`: Number of runs
  * `s`: Minimum number of successes to consider a hit

# Optional Inputs

  * `a`: If `true`, ignore MAFs. By default (`a=false`) the sites are selected at random weighted by their MAFs.
