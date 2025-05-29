```
filecontains(needle)
```

A `StackFrame` filter that returns `true` if the given `StackFrame` has `needle` in its file path.

# Example

```julia-repl
julia> stackframe = stacktrace()[1]
top-level scope at REPL[6]:1

julia> stackframe.file
Symbol("REPL[6]")

julia> filecontains("REPL")(stackframe)
true
```

See also: [`StackTraces.StackFrame`](@ref)
