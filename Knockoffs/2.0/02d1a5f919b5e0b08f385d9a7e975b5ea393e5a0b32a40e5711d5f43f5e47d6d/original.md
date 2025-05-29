```
hmm_knockoff(plinkname; [datadir], [plink_outfile], [fastphase_outfile], [outdir], [verbose], args...)
```

Generates HMM knockoffs from binary PLINK formatted files. This is done by first running fastPHASE, then running Algorithm 2 of "Gene hunting with hidden Markov model knockoffs" by Sesia, Sabatti, and Candes

# Input

  * `plinkname`: Binary PLINK file names without the `.bed/.bim/.fam` suffix.

# Optional arguments

  * `datadir`: Full path to the PLINK and fastPHASE files (default = current directory)
  * `plink_outfile`: Output PLINK format name
  * `fastphase_outfile`: The output file name from fastPHASE's alpha, theta, r files
  * `args...`: Any parameter that accepted in `fastPHASE.fastphase_estim_param()`

# Output

  * `plink_outfile.bed`: `n × p` knockoff genotypes
  * `plink_outfile.bim`: SNP mapping file. Knockoff have SNP names ending in ".k"
  * `plink_outfile.fam`: Sample mapping file, this is a copy of the original `plinkname.fam` file
  * `fastphase_outfile_rhat.txt`: averaged r hat file from fastPHASE
  * `fastphase_outfile_alphahat.txt`: averaged alpha hat file from fastPHASE
  * `fastphase_outfile_thetahat.txt`: averaged theta hat file from fastPHASE
