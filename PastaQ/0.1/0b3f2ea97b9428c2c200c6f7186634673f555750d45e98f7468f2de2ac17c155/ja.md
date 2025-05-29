```
split_dataset(data::Matrix; train_ratio::Float64 = 0.9, randomize::Bool = true)
```

データセットを `train` と `test` セットに分割します。`train_ratio`（すなわち `train_data` におけるデータの割合）を指定します。`randomize=true`（デフォルト）であれば、分割する前に `data` がランダムにシャッフルされます。
