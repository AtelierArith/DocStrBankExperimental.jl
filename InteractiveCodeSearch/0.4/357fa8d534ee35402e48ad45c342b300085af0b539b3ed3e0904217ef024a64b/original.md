```
@search x [:shallow | :s | :recursive | :r]
```

List file locations at which `x` are defined in an interactive matcher and then open the chosen location in the editor.

When `x` is a module, only the top-level definitions are searched.  To search all definitions in the submodule, pass `:recursive` or `:r` flag.

```
@search
```

If no expression is provided, search for the method returned by the previous execution; i.e., `x` defaults to `ans`.

# Examples

```julia
@search show                      # all method definitions
@search @time                     # all macro definitions
@search Base.Enums                # methods and macros in a module
@search REPL :r                   # search the module recursively
@search *(::Integer, ::Integer)   # methods with specified types
@search dot(π, ℯ)                 # methods with inferred types
```

Note that `@search` evaluates complex expression with `.` and `[]` such as follows and search the returned value or the type of it:

```julia
@search Base.Multimedia.displays[2].repl
```
