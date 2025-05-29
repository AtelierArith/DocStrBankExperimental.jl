```
symparseeval(s::String)
```

Parse `s` into Julia expressions, translates them to Symata expressions, and Symata-evaluates each one, returning the value returned by the final evaluation.

See `symparsestring`, `symtranseval`, and `@sym`.
