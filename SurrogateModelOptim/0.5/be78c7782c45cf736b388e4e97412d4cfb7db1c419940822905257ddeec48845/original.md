```
scaled_LHC_sampling_plan(search_range::Array{Tuple{Float64,Float64},1},num_samples,sampling_plan_opt_gens;trace::Symbol=:silent)
```

Create a Latin Hypercube sampling plan scaled to the `search_range` where  `size(plan) = (num_dimensions,num_samples)`.
