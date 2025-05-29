```
load_credit_default(
    n::Union{Nothing,Int}=5000;
    seed=data_seed,
    train_test_split::Union{Nothing,Real}=nothing,
    shuffle::Bool=false,
    return_cats::Bool=false,
)
```

UCIクレジットデフォルトデータを読み込みます。
