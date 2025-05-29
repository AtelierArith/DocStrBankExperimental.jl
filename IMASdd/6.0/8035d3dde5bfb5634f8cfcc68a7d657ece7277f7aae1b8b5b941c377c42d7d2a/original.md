```
refreeze!(@nospecialize(ids::T), field::Symbol, @nospecialize(default::Any=missing)) where {T<:IDS}
```

If the ids field has an expression associated with, it re-evaluates it in place.

If the expression fails, a default value will be assigned.
