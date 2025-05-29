```
cast(lk::Link, args2...)
cast(name::Symbol, args2...)
```

Cast `args2...` to the actor `lk` (or `name` if registered)  to execute its behavior with `args2...` without sending a  response. 

**Note:** you can prompt the returned value with [`query`](@ref).
