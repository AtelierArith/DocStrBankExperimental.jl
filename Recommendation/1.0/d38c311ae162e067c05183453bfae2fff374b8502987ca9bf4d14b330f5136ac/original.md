```
load_movielens_latest([path=nothing]) -> DataAccessor
```

`path` points to a locally saved [MovieLens Latest (Small)](https://files.grouplens.org/datasets/movielens/ml-latest-small-README.html). Read user-item-rating triples in the folder, and convert them into a `DataAccessor` instance.

Download and decompress a corresponding zip file, if `path` is not given or the specified folder does not exist.
