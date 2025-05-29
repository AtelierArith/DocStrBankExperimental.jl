```
Lexer{E,OQ,CQ,NL,IO_t}

Lexer(io, escapechar, openquotechar, closequotechar, newline) -> Lexer{E,OQ,CQ,NL,IO_t}
Lexer(io, nothing, newline) -> Lexer{Nothing,Nothing,Nothing,NL,IO_t}
```

A stateful lexer type for newline detection. Use with the `find_newlines!` function. The type parameters are:

  * `E`: the escape character
  * `OQ`: the open quote character
  * `CQ`: the close quote character
  * `NL`: the newline character
  * `IO_t`: the type of the IO object, e.g. `IOBuffer` or `IOStream`

Either `E`, `OQ`, and `CQ` are all `Nothing`, or they are all single-byte characters.

When `E`, `OQ`, and `CQ` are not `Nothing`, the lexer will find all newlines in the input, that are not inside a string (between two quotes). This is useful for finding record separators in CSVs.

If they are all `Nothing`, the lexer will be quote-unaware, and find all newlines in the input, regardless of whether they are inside a string or not. You can construct such a lexer with `Lexer(io, nothing, newline)`.
