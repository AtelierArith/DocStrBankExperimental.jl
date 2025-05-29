```
abc_model_choice_dataset(models,
                         summary_stats_observations,
                         summary_stats_func::Function, distance_func::Function,
                         k::Int, N_ref::Int; dir_results::Union{Nothing,String} = nothing)
```

Creates a reference table for ABC model choice with discrete uniform prior distribution over the models.
