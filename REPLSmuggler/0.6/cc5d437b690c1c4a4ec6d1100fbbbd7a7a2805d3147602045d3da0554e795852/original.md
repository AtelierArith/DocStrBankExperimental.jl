```
smuggle(stacks::Base.ExceptionStack)
```

Smuggle an exception stack. In the Julia REPL the `err` variable is implicitly defined and contains the stack from the last thrown error.

# Examples

```julia-repl
julia> error("foo")
ERROR: foo
Stacktrace:
[...]

julia> smuggle(err)
```
