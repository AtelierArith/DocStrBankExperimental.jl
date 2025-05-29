```
Base.deleteat!(@nospecialize(ids::T), condition::Pair{String}, conditions::Pair{String}...) where {T<:IDSvector}
```

If an entry matching the condition is found, then the content of the matching IDS is emptied
