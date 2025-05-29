```
is_valid(x, encoding::Symbol = :none)
```

Check if `x` has a valid format for `encoding`.

For instance, if `encoding == :one_hot`, at most one bit of `x` can be set to 1.
