```
inner_price_elasticities(;problem, 
    frac_results = [], 
    linear::Vector{String}, 
    nonlinear::Vector{String}, 
    by_var::String = "", 
    monte_carlo_draws = 50, 
    product = 1)
```

This function is called by `price_elasticities!` and is not intended to be called directly by the user. It is an intermediate function that passes the relevant arguments into `all_elasticities` and returns the results to be processed and re-shaped.
