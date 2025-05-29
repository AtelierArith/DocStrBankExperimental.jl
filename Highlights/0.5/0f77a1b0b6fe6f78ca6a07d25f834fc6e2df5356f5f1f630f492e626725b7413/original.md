```julia
lexer(name)

```

Return the `AbstractLexer` associated with the lexer named `name`. `name` must be a string. Internally this checks the `:aliases` field in each lexer definition to see whether it is a match.

!!! warning
    This method is *not* type stable.


When no lexer matches the given `name` an `ArgumentError` is thrown.
