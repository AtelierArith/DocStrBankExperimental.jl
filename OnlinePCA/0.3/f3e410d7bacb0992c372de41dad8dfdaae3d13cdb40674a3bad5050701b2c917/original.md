```
tenxsumr(; tenxfile::AbstractString="", outdir::AbstractString=".", group::AbstractString="", chunksize::Number=5000)
```

Extract the summary information of 10X-HDF5.

## Input Arguments

  * `tenxfile` is the HDF5 file formatted by 10X Genomics.
  * `outdir` is specified the directory you want to save the result.
  * `group` is the group name of HDF5 (e.g. mm10).
  * `chunksize` is the number of rows reading at once (e.g. 5000).

## Output Files

  * `Sample_NoCounts.csv` : Sum of counts in each column.
  * `Feature_Means.csv` : Mean in each row.
  * `Feature_LogMeans.csv` : Log10(Mean+1) in each row.
  * `Feature_SqrtMeans.csv` : sqrt(Mean+1) in each row.
  * `Feature_Vars.csv` : Sample variance in each row.
  * `Feature_LogVars.csv` : Log10(Var+1) in each row.
  * `Feature_SqrtVars.csv` : sqrt(Var+1) in each row.
  * `Feature_CV2s.csv` : Coefficient of Variation in each row.
