```
freeze(@nospecialize(ids::T)) where {T<:Union{IDS,IDSvector}}
```

Return a new IDS with all expressions evaluated (data is copied)

NOTE: Expressions that fail will be `missing`
