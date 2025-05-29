```
get_geno_completecases(data_missing::GeneticStudyData) -> GeneticStudyData
```

Identify and remove rows or columns from a data structure `GeneticStudyData` containing missing values in geno,  prioritizing those with the highest percentage of missing data.

# Arguments

  * `data_missing`: A genetic study data structure containing possibly missing values.

# Returns

  * `GeneticStudyData`: A new genetic study data structure with the same fields as the input, but where rows and columns

with missing data have been systematically removed until no missing data remains.

# Description

The core of the function involves iteratively identifying and removing rows or columns with the highest percentage of missing data in the geno object. This decision is based on whether the maximum percentage of missing data across rows exceeds that across columns. Rows or columns are removed until there are no missing values left in the matrix.

After cleaning, the function reconstructs the `GeneticStudyData` data structure.  It ensures the data aligns with the expected format by adjusting the dimensions of the data, regrouping by chromosomes,  and ensuring marker and sample identifiers are correctly aligned.
