`compress_save!(mod::Module, SD::SourceData; move_source = true, targeting_mod = false)` compress the `SD.srcfile`, save the zipped one to `SD.zipfile`, and update the `dataset_table(mod)`.

Options:

  * By default, `move_source = true` that the source file will be moved to `dir_raw()`.
  * Set `targeting_mod = true` to make sure the compressed data is saved relative to the repo of `mod`. Default is `false`, which means you can compress and save the data to whatever directory you like.

`compress_save!` returns `SD::SourceData` of relative paths to `DATASET_ABS_DIR(mod)[]`, where `relpath!` is applied that paths `SD` as well as `dataset_table(mod)` are modified to be relative.

# Example

```julia
using YourDatasets, SmallDatasetMaker
compress_save!(YourDatasets, SD; targeting_mod = true)
```

This do the followings:

1. Create zipped files under `data/` of package `YourDatasets` in `dev`elopment.
2. Move the source file `SD.srcfile` (i.e., the raw .csv data) to `dir_raw(YourDatasets, ...)` by default.
3. Add a new line to `SmallDatasetMaker.dataset_table(YourDatasets)` (update `data/doc/datasets.csv` of `YourDatasets`).

See also `SourceData`, `compress_save`.
