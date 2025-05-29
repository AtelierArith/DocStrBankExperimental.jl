```
get_geno_completecases(geno_missing::Geno) -> Geno
```

Identify and remove rows or columns from a genotype data structure `Geno` containing missing values,  prioritizing those with the highest percentage of missing data.

# Arguments

  * `geno_missing::Geno`: A genotype data structure containing possibly missing values.

# Returns

  * `Geno`: A new genotype data structure with the same fields as the input, but where rows and columns

with missing data have been systematically removed until no missing data remains.

# Description

The core of the function involves iteratively identifying and removing rows or columns with the highest percentage of missing data.  This decision is based on whether the maximum percentage of missing data across rows exceeds that across columns.  Rows or columns are removed until there are no missing values left in the matrix.

After cleaning, the function reconstructs the `Geno` data structure.  It ensures the data aligns with the expected format by adjusting the dimensions of the data, regrouping by chromosomes,  and ensuring marker and sample identifiers are correctly aligned.
