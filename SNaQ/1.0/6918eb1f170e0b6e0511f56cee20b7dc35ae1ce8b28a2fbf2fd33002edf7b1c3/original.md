```
readtableCF(file)
readtableCF(data frame)
readtableCF!(data frame)
```

Read a file or DataFrame object containing a table of concordance factors (CF), with one row per 4-taxon set. The first 4 columns are assumed to give the labels of the 4 taxa in each set (tx1, tx2, tx3, tx4). Columns containing the CFs are assumed to be named `CF12_34`, `CF13_24` and `CF14_23`; or `CF12.34`, `CF13.24` and `CF14.23`; or else are assumed to be columns 5,6,7. If present, a column named 'ngenes' will be used to get the number of loci used to estimate the CFs for each 4-taxon set.

Output: [`DataCF`](@ref) object

Optional arguments:

  * `summaryfile`: if specified, a summary file will be created with that name.
  * `delim` (for the first form only): to specify how columns are delimited, with single quotes: delim=';'. Default is a `csv` file, i.e. `delim=','`.
  * `mergerows`: false by default. When true, will attempt to merge multiple rows corresponding to the same four-taxon set (by averaging their quartet CFs) even if none of the species is repeated within any row (that is, in any set of 4 taxa)

The last version modifies the input data frame, if species are represented by multiple alleles for instance (see [`readtableCF!`](@ref)(data frame, columns)).
