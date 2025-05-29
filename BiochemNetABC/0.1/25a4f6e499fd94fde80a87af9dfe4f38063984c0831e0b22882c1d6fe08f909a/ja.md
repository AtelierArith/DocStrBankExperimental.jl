```
abc_model_choice_dataset(models,
                         summary_stats_observations,
                         summary_stats_func::Function, distance_func::Function,
                         k::Int, N_ref::Int; dir_results::Union{Nothing,String} = nothing)
```

モデルに対する離散一様事前分布を持つABCモデル選択のための参照テーブルを作成します。
