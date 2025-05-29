`compress_save(mod::Module, srcpath; args...)` is equivalent to `compress_save!(mod, SourceData(srcpath))` but returns `SD = SourceData(srcpath)`.

`compress_save` takes the same keyword arguments as `compress_save!`, which returns `SD::SourceData` of relative paths to `DATASET_ABS_DIR(mod)[]`.

# Example

```julia
using YourDatasets, SmallDatasetMaker
srcfile = "data/raw/Category_A/Dataset_B.csv" # path to the .csv to be compressed.
compress_save(YourDatasets, srcfile; targeting_mod = true)
```
