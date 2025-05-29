```
load_german_credit(
    n::Union{Nothing,Int}=nothing;
    seed=data_seed,
    train_test_split::Union{Nothing,Real}=nothing,
    shuffle::Bool=false,
)
```

UCIドイツ信用データを読み込みます。
