`package_name`や`dataset_name`が指定されていない場合、`(package_name, dataset_name) = get_package_dataset_name(srcfile)`が適用されます。

# 例

```
using SmallDatasetMaker
srcfile = "data/raw/Category_A/Dataset_B.csv" # 圧縮される.csvへのパス。
SD = SourceData(srcfile)
```
