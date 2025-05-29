`cleantable(mod::Module)` は `dataset_table(mod)` の冗長なエントリを削除し、**data/doc/datasets.csv** を上書きします。注意して使用し、コミットおよびプッシュする前に確認してください。

# 例

```julia
using SmallDatasetMaker, YourDatasets
SmallDatasetMaker.cleantable(YourDatasets)
```
