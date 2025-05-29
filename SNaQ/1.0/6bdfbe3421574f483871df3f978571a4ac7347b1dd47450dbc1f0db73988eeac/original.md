```
readtableCF!(data frame, columns; mergerows=false)
```

Read in quartet CFs from data frame, assuming information is in columns numbered `columns`, of length **7 or 8**: 4 taxon labels then 3 CFs then ngenes possibly.

If some species appears more than once in the same 4-taxon set (e.g. t1,t1,t2,t3), then the data frame is modified to remove rows (4-taxon sets) that are uninformative about between-species relationships. This situation may occur if multiple individuals are sampled from the same species. A 4-taxon set is uninformative (and its row is removed) if one taxon is repeated 3 or 4 times (like t1,t1,t1,t1 or t1,t2,t2,t2). The list of species appearing twice in some 4-taxon sets is stored in the output DataCF object. For these species, the length of their external edge is identifiable (in coalescent units). If multiple rows correspond to the same 4-taxon set, these rows are merged and their CF values (and number of genes) are averaged. If none of the species is repeated within any 4-taxon set, then this averaging is attempted only if `mergerows` is true.

```
readtableCF!(DataCF, data frame, columns)
```

Modify the `.quartet.obsCF` values in the `DataCF` object with those read from the data frame in columns numbered `columns`. `columns` should have **3** columns numbers for the 3 CFs in this order: `12_34`, `13_24` and `14_23`.

Assumptions:

  * same 4-taxon sets in `DataCF` and in the data frame, and in the same order, but this assumption is *not checked* (for speed, e.g. during bootstrapping).
  * one single row per 4-taxon set (multiple individuals representatives of the same 4-taxon set should have been already merged); basically: the DataCF should have been created from the data frame by `readtableCF!(df, colums)`
