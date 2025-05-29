```
load_movielens_100k([path=nothing]) -> DataAccessor
```

`path` points to a locally saved [MovieLens 100k](https://grouplens.org/datasets/movielens/100k/). Read user-item-rating triples in the folder, and convert them into a `DataAccessor` instance.

Download and decompress a corresponding zip file, if `path` is not given or the specified folder does not exist.
