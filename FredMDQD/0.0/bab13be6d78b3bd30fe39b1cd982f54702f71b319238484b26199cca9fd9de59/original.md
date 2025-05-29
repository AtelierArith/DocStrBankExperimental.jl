```
search_appendix(s::Symbol, args..., kwargs...)
```

Search the appendix for variable names. 

## Arguments

  * `s::Symbol`: Should be `:MD` for Fred MD and `:QD` for Fred QD.
  * `needle::Union{String, Regex}`: Pattern to find in the appendix.

## Keyword Arguments

  * `case_sensitive::Bool=false`: Should the search be case sensitive?
  * `historic::Bool=false`: Should the search be in the current or historic appendix?

## Returns

  * Returns a `DataFrame` of all the matches in the appendix.
