```
decision_by_name(stochasticprogram::Stochasticprogram,
                 stage::Integer,
                 name::String)::Union{AbstractVariableRef, Nothing}
```

Returns the reference of the variable with name attribute `name` at `stage` of `stochasticprogram` or `Nothing` if no variable has this name attribute. Throws an error if several variables have `name` as their name attribute at stage `s`.
