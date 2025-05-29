```
count(T::Type{<:Relational}; kwargs...)
count(T::Type{<:Relational}, cond::String; kwargs...)
count(T::Type{<:Relational}, cond::Pair; kwargs...)
count(T::Type{<:Relational}, conds::Union{Tuple,AbstractArray}; kwargs...)
```

Gets the count of matching records.
