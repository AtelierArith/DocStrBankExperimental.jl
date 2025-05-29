```
VolData_combined = combine_vol_data(VolData::NamedTuple; lat=nothing, lon=nothing, depth=nothing, dims=(100,100,100), dataset_preferred = 1)
```

これは異なるボリュメトリックデータセット（`VolData`で指定）を取り込み、それらを1つのデータセットに統合します。NamedTuple内で「参照」データセット（`dataset_preferred`）を提供するか、新しいデータセットの緯度/経度/深さおよび寸法を提供する必要があります。
