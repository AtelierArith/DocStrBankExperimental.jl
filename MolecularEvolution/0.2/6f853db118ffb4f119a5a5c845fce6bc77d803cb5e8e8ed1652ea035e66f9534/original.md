```
leaf_samples(tree; partition_inds = 1)
```

Returns the result of `partition2obs` for each leaf of the tree. Can be used eg. after `sample_down!` is called. If using a eg. codon model, this will extract a string from the CodonPartition on each leaf. Acts upon the first partition by default, but this can be changed by setting `partition_inds`, which can also be a vector of indices,  in which case the result will be a vector for each leaf.
