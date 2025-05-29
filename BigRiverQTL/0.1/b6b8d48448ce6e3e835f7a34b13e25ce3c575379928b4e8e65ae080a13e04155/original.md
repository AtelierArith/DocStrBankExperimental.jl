```
summary_missing(geno_missing::Geno; issorted::Bool = false) -> (missing_per_row::DataFrame, missing_per_col::DataFrame)
```

Calculate the percentage of missing data for each sample and each marker in a genetic dataset.

# Arguments

  * `geno_missing::Geno`: A genetic data structure of type Geno.
  * `issorted::Bool = false`: An optional boolean flag indicating whether to sort the results by   the percentage of missing data in descending order.

# Returns

  * `(missing_per_row::DataFrame, missing_per_col::DataFrame)`: A tuple of two `DataFrame`s:

      * `missing_per_row`: Each row represents a sample with columns for sample identifiers and the percentage of missing data.
      * `missing_per_col`: Each row represents a marker with columns for marker names and the percentage of missing data.
