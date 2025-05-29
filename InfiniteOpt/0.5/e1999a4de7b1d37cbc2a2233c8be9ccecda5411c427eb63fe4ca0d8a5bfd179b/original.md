```
JuMP.object_dictionary(model::InfiniteModel)::Dict{Symbol, Any}
```

Return the dictionary that maps the symbol name of a macro defined object (e.g.,  a parameter, variable, or constraint) to the corresponding object. Objects are  registered to a specific symbol in the macros. For example,  `@variable(model, x[1:2, 1:2])` registers the array of variables `x` to the symbol `:x`.
