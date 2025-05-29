```
load_uci_adult(
    n::Union{Nothing,Int}=1000;
    seed=data_seed,
    return_cats::Bool=false,
    train_test_split::Union{Nothing,Real}=nothing,
    shuffle::Bool=false,
)
```

UCI 'Adult' データセットからデータを読み込みます。
