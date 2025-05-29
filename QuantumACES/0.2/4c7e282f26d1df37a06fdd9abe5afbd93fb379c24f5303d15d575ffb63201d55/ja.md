```
load_aces(d::Design, budget_set::Vector{Int})
load_aces(circuit_param::AbstractCircuitParameters, noise_param::AbstractNoiseParameters, tuple_number::Integer, repeat_numbers::Vector{Int}, full_covariance::Bool, ls_type::Symbol, budget_set::Vector{Int})
```

指定された変数によってファイル名が指定されたACESデータをロードします。
