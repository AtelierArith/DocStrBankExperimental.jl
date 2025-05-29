```
split_dataset(data::Matrix; train_ratio::Float64 = 0.9, randomize::Bool = true)
```

Split a data set into a `train` and `test` sets, given a `train_ratio` (i.e. the percentage of data in `train_data`. If `randomize=true` (default), the `data` is randomly shuffled before splitting.
