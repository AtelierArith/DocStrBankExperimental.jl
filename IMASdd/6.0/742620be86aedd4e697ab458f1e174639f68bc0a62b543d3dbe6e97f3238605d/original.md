```
unfreeze!(@nospecialize(ids::T), field::Symbol) where {T<:IDS}
```

If the ids field has an expression associated with it, that was frozen, turn it back into an expression.
