```
render([io], tokens, view)
render([io], tokens; kwargs...)
(tokens::MustacheTokens)([io]; kwargs...)
```

Render a set of tokens with a view, using optional `io` object to print or store.

## Arguments

  * `io::IO`: Optional `IO` object.
  * `tokens`: Either Mustache tokens, or a string to parse into tokens
  * `view`: A view provides a context to look up unresolved symbols demarcated by mustache braces. A view may be specified by a dictionary, a module, a composite type, a vector, a named tuple, a data frame, a `Tables` object, or keyword arguments.

!!! note
    The `render` method is currently exported, but this export may be deprecated in the future.

