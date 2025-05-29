```
update_corrfns!(tracker, value, index)
```

This function is equivalent to writing `tracker[index] = value` with exception that it also returns a rollback handle which can fastly bring the tracker to the previous state by calling `rollback!`.

See also: [`rollback!`](@ref).
