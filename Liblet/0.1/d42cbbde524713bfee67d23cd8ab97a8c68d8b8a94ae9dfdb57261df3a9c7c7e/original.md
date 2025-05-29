```
suchthat(;left::AbstractString = nothing, right::AbstractString = nothing, rightlen::Int = nothing, right_is_suffix_of::AbstractString = nothing)::Array
```

A predicate (that is a one-argument function that retuns `true` or `false`) that is `true` weather the production given as argument satisfies all the predicates given by the named arguments.
