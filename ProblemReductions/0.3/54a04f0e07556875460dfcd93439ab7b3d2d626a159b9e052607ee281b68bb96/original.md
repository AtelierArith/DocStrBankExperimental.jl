```
num_flavors(::Type{<:AbstractProblem}) -> Int
num_flavors(::GT) where GT<:AbstractProblem -> Int
```

Returns the number of flavors (domain) of a degree of freedom.
