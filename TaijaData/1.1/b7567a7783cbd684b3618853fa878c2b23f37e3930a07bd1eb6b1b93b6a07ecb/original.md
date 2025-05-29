```
load_uci_adult(
    n::Union{Nothing,Int}=1000;
    seed=data_seed,
    return_cats::Bool=false,
    train_test_split::Union{Nothing,Real}=nothing,
    shuffle::Bool=false,
)
```

Loads data from the UCI 'Adult' dataset.
