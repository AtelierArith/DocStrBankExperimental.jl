```
fun(f::Function, args...; kwargs...)
```

Save a function `f` and its arguments in a closure for later execution.

# Arguments

The arguments `args...` and keyword arguments `kwargs...` to fun are passed to `f` at execution but may change their values between beeing captured in `fun` and `f`s later execution. If `f` needs their current values at execution time there are two possibilities:

1. `fun` can take `fun`s, function closures, symbols or expressions at the place of values  or variable arguments. They are evaluated at event time just before being passed to f.  There is one exception: if `f` is an `event!`, its arguments are passed on unevaluated.
2. A mutable type argument (Array, struct ...) is always current. You can  also change its content from within a function.

If using `Symbol`s or `Expr` in `fun` you get a one time warning. They are  evaluated at global scope in Module `Main` only and therefore cannot be used by other modules.
