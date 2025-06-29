```
sumr(; binfile::AbstractString="", outdir::AbstractString=".", pseudocount::Number=1.0, mode::AbstractString="dense", chunksize::Int=1)
```

Extract the summary information of data matrix.

## Input Arguments

  * `binfile` is a Julia Binary file generated by `csv2bin` function.
  * `outdir` is specified the directory you want to save the result.
  * `pseudocount` is specified to avoid NaN by log10(0) and used when `Feature_LogMeans.csv` <log10(mean+pseudocount) value of each feature> is generated.
  * `mode` : "dense" or "sparse_mm" can be specified.
  * `chunksize` : The number of rows to be read at once.

## Output Files

  * `Sample_NoCounts.csv` : Sum of counts in each column.
  * `Feature_Means.csv` : Mean in each row.
  * `Feature_LogMeans.csv` : Log10(Mean+pseudocount) in each row.
  * `Feature_FTTMeans.csv` : FTT(Mean+pseudocount) in each row.
  * `Feature_Vars.csv` : Sample variance in each row.
  * `Feature_LogVars.csv` : Log10(Var+pseudocount) in each row.
  * `Feature_FTTVars.csv` : FTT(Var+pseudocount) in each row.
  * `Feature_CV2s.csv` : Coefficient of Variation in each row.
  * `Feature_NoZeros.csv` : Number of zero-elements in each row.
