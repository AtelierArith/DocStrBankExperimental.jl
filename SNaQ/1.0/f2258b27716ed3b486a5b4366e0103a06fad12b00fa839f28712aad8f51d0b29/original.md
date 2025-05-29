```
DataCF
```

type that contains the following attributes:

  * `quartet` (vector of Quartets)
  * `numQuartets`
  * `tree` (vector of trees: empty if a table of CF was input instead of list of trees)
  * `numTrees` (-1 if a table CF was input instead of list of trees)
  * `repSpecies` (taxon names that were repeated in table of CF or input gene trees: used inside snaq for multiple alleles case)

The list of `Quartet` may be accessed with the attribute `.quartet`. If the input was a list of trees, the `HybridNetwork`'s can be accessed with the attribute `.tree`. For example, if the `DataCF` object is named `d`, `d.quartet[1]` will show the first quartet and `d.tree[1]` will print the first input tree.
