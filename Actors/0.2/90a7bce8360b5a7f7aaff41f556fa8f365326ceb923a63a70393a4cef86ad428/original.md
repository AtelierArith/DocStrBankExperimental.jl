```
call(lk::Link, [from::Link,] args2...; timeout::Real=5.0)
call(name::Symbol, ....)
```

Call an actor to execute its behavior and to send a  [`Response`](@ref) with the result. 

# Arguments

  * actor `lk::Link` (or `name::Symbol` if registered),
  * `from::Link`: sender link,
  * `args2...`: remaining arguments to the actor.
  * `timeout::Real=5.0`: timeout in seconds.

**Note:** If `from` is omitted, `call` blocks and returns the result
