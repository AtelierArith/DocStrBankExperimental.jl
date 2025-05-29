```
JuMP.reduced_cost(vref::GeneralVariableRef)
```

Extend `JuMP.reduced_cost`. This returns the reduced cost(s) of a variable. This  will be a vector of scalar values for an infinite variable or will be a scalar  value for finite variables. 

**Example**

```julia-repl
julia> reduced_cost(x)
12.81
```
