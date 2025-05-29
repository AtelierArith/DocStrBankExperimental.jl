```
MultiRow(n::Int, vpos::Symbol, cell::Any, width::String)
MultiRow(n, vpos, cell; width="*")
```

For `\multirow[vpos]{n}{width}{cell}`. Use the symbols `:t`, `:c`, `:b` for `vpos`.
