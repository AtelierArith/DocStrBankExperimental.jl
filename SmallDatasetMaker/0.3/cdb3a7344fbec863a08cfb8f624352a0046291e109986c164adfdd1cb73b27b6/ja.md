`compress_save(mod::Module, srcpath; args...)` は `compress_save!(mod, SourceData(srcpath))` と同等ですが、`SD = SourceData(srcpath)` を返します。

`compress_save` は `compress_save!` と同じキーワード引数を取り、`DATASET_ABS_DIR(mod)[]` への相対パスの `SD::SourceData` を返します。

# 例

```julia
using YourDatasets, SmallDatasetMaker
srcfile = "data/raw/Category_A/Dataset_B.csv" # 圧縮される .csv へのパス。
compress_save(YourDatasets, srcfile; targeting_mod = true)
```
