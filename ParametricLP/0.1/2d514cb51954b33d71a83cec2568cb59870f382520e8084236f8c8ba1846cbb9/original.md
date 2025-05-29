```
find_regions(
    model::JuMP.Model,
    parameters::Vector{VariableRef},
    box::Tuple{Tuple{Float64,Float64},Tuple{Float64,Float64}},
    ϵ = 0.01,
)
```

This function finds all the optimal bases and their corresponding regions in terms of two `parameters` in a linear programming `model`.

### Required arguments

`model` is a `JuMP.Model` linear programme, defined in a way where two of the right-hand side values are replaced by variables.

`parameters` is a vector of two variables that appear on the right-hand side of the two constraints that we wish to explore parametrically.

`box` is a Tuple of Tuples, this defines the minimum and maximum value for each of the `parameters` described above.

### Optional arguments

`ϵ` is a tolerance value used when ensuring that we find an adjacent basis.
