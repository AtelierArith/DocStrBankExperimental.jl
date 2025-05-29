```
make_vector_fold(pattern, gap, fold, kind = :mutable)
```

A dispatcher to construct a folded vector. The `kind` of vector can be set to either `:mutable` (default) or `:immutable`. The default is faster in most cases but it depends on the `pattern`, `gap`, and `fold` parameters. For critical code, it is recommended to benchmark both options.
