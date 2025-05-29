```
empiricalDNAfrequencies(DNAdata::AbstractDataFrame, DNAweights,
                        correction=true, useambiguous=true)
```

Estimate base frequencies in DNA data `DNAdata`, ordered ACGT.

  * `DNAdata`: data frame. All columns are used. If the first column gives species names, find a way to ignore it before calculating empirical frequencies, e.g. `empiricalDNAfrequencies(view(DNAdata, :, 2:size(DNAdata, 2)))`. Data type must be `BioSymbols.DNA` or `Char` or `String`. WARNING: this is checked on the first column only.
  * `DNAweights`: vector of weights, to weigh each column in `DNAdata`.
  * `correction`: if `true`, add 1 to each count and 4 to the denominator for a more stable estimator, similar to Bayes prior of 1/4 and the Agresti-Coull interval in binomial estimation.
  * `useambiguous`: if `true`, ambiguous bases are used (except gaps and Ns). For example, `Y` adds 0.5 weight to `C` and 0.5 weight to `T`.
