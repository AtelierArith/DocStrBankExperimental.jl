`cleantable(mod::Module)` remove redundant entries of the `dataset_table(mod)` **and overwrite** `data/doc/datasets.csv`. Use with caution and verify before commit & push.

# Example

```julia
using SmallDatasetMaker, YourDatasets
SmallDatasetMaker.cleantable(YourDatasets)
```
