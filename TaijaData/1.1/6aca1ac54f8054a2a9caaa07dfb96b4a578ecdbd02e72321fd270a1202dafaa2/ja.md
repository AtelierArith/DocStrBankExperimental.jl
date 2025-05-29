```
load_california_housing(
    n::Union{Nothing,Int}=5000;
    seed=data_seed,
    train_test_split::Union{Nothing,Real}=nothing,
    shuffle::Bool=false,
)
```

カリフォルニア住宅データを読み込みます。
