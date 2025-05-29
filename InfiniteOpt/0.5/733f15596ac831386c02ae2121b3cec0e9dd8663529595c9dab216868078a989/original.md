```
JuMP.add_variable(model::InfiniteModel, var::SemiInfiniteVariable,
                  [name::String = ""])::GeneralVariableRef
```

Extend the `JuMP.add_variable` function to accomodate `InfiniteOpt`  semi-infinite variable types. Adds `var` to the infinite model `model` and  returns a [`GeneralVariableRef`](@ref). Primarily intended to be an internal  function used in evaluating measures.
