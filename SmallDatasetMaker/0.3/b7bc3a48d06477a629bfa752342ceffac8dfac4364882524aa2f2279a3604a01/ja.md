`compress_save!(mod::Module, SD::SourceData; move_source = true, targeting_mod = false)` は `SD.srcfile` を圧縮し、圧縮されたファイルを `SD.zipfile` に保存し、`dataset_table(mod)` を更新します。

オプション:

  * デフォルトでは、`move_source = true` であり、ソースファイルは `dir_raw()` に移動されます。
  * `targeting_mod = true` を設定すると、圧縮されたデータが `mod` のリポジトリに対して相対的に保存されることが保証されます。デフォルトは `false` であり、これはデータを好きなディレクトリに圧縮して保存できることを意味します。

`compress_save!` は `DATASET_ABS_DIR(mod)[]` に対する相対パスの `SD::SourceData` を返します。ここで、`relpath!` が適用され、`SD` および `dataset_table(mod)` のパスが相対的に変更されます。

# 例

```julia
using YourDatasets, SmallDatasetMaker
compress_save!(YourDatasets, SD; targeting_mod = true)
```

これにより、以下のことが行われます:

1. パッケージ `YourDatasets` の `data/` に圧縮ファイルが作成されます。
2. ソースファイル `SD.srcfile`（すなわち、生の .csv データ）がデフォルトで `dir_raw(YourDatasets, ...)` に移動されます。
3. `SmallDatasetMaker.dataset_table(YourDatasets)` に新しい行が追加されます（`YourDatasets` の `data/doc/datasets.csv` が更新されます）。

`SourceData`、`compress_save` も参照してください。
