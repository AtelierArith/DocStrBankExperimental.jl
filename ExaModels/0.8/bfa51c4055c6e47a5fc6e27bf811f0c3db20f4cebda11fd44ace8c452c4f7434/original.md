```
multipliers_U(result, x)
```

Returns the multipliers_U for variable `x` associated with `result`, obtained by solving the model.

## Example

```jldoctest
julia> using ExaModels, NLPModelsIpopt

julia> c = ExaCore();

julia> x = variable(c, 1:10, lvar = -1, uvar = 1);

julia> objective(c, (x[i]-2)^2 for i in 1:10);

julia> m = ExaModel(c);

julia> result = ipopt(m; print_level=0);

julia> val = multipliers_U(result, x);

julia> isapprox(val, fill(2, 10), atol=sqrt(eps(Float64)), rtol=Inf)
true
```
