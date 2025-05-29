```
name_to_function(model::InfiniteModel, name::Symbol, num_args::Int)::Union{Function, Nothing}
```

Return the registered function that corresponds to `name` with `num_args`.  Returns `nothing` if no such registered function exists. This helps retrieve the  functions of function names stored in `NLPExpr`s.
