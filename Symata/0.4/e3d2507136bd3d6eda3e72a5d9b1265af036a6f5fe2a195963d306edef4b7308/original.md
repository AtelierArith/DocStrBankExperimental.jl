```
@extomx(ex)
```

inserts translation of Julia expression `ex` to Symata into code. This is used in Symata code. For instance in `Collect` in `algebra.jl`.

`@extomx` differs from `@sym` in that it does not evaluate the resulting Symata expression.
