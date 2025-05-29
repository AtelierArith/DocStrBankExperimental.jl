```
freeze!(@nospecialize(ids::T)) where {T<:Union{IDS,IDSvector}}
```

Evaluates all expressions in place

NOTE: Expressions that fail will be `missing`
