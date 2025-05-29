```
expect(expr::JuMP.AbstractJuMPScalar,
       prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef};
       [num_supports::Int = DefaultNumSupports])::GeneralVariableRef
```

Makes a measure for `expr` based on its expectation with respect to `prefs`. For  `prefs` with distribution domains this is essentially equivalent to 

```julia
1/total_num_supports * support_sum(expr, prefs, label = WeightedSample)
```

Thus, for these domain types it only considers supports that are added to `prefs`  via generation on creation (i.e., specifying the `num_supports` keyword when  creating `prefs`). For incorporating other supports consider  calling [`integral`](@ref) and using the `weight_func` argument to specify the  probability density function.

For a single infinite parameter defined over a bounded interval domain the syntax  becomes:

```julia
    expect(expr::JuMP.AbstractJuMPScalar,
           prefs::GeneralVariableRef;
           [num_supports::Int = DefaultNumSupports,
           pdf::Function = (supp) -> 1 / (ub - lb)])::GeneralVariableRef
```

The behavior with the default `pdf` is equivalent to evaluating the mean value  theorem for integrals for `expr` with respect to `pref` using  [`UniTrapezoid`](@ref). Other density functions can be given via `pdf`. Errors  if the interval domain is not bounded.

Note that num_supports should be 0 if a single dependent parameter is given. Also, note that it is preferred to call [`@expect`](@ref) when `expr` is not just a single variable reference.

**Example**

```julia-repl
julia> @infinite_parameter(model, x ~ Normal(), num_supports = 2)
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> meas = expect(f, x)
𝔼{x}[f(x)]

julia> expand(meas)
0.5 f(0.6791074260357777) + 0.5 f(0.8284134829000359)
```
