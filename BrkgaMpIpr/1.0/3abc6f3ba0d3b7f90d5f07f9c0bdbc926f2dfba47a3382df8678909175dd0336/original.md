```
set_bias_custom_function!(brkga_data::BrkgaData, bias_function::Function)
```

Set a new bias function to be used to rank the chromosomes during the mating. **It must be a positive non-increasing function** returning a Float64, i.e., `f(::Int64)::Float64` such that `f(i) ≥ 0` and `f(i) ≥ f(i+1)` for `i ∈ [1..total_parents]`. For instance, the following sets an inverse quadratic function:

```julia
set_bias_custom_function!(brkga_data, x -> 1.0 / (x * x))
```

# Throws

  * `ArgumentError`: in case the function is not a non-increasing positive function.
