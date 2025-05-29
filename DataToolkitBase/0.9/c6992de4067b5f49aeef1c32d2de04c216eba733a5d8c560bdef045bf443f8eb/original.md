```
EmptyStackError()
```

An attempt was made to perform an operation on a collection within the data stack, but the data stack is empty.

# Example occurrence

```julia-repl
julia> getlayer(nothing) # with an empty STACK
ERROR: EmptyStackError: The data collection stack is empty
Stacktrace: [...]
```
