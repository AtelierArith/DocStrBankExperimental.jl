```
inner_price_elasticities(;problem, 
    frac_results = [], 
    linear::Vector{String}, 
    nonlinear::Vector{String}, 
    by_var::String = "", 
    monte_carlo_draws = 50, 
    product = 1)
```

この関数は `price_elasticities!` によって呼び出され、ユーザーが直接呼び出すことを意図していません。これは中間関数であり、関連する引数を `all_elasticities` に渡し、結果を処理および再形成するために返します。
