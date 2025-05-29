If `package_name, dataset_name` not specified, `(package_name, dataset_name) = get_package_dataset_name(srcfile)` is applied.

# Example

```
using SmallDatasetMaker
srcfile = "data/raw/Category_A/Dataset_B.csv" # path to the .csv to be compressed.
SD = SourceData(srcfile)
```
