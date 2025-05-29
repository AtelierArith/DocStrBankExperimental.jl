```
@return_if_exception(ex)
```

Evalutes the destructured assignment expression `ex` of the form `(; names...) = rhs` or `(names...) = rhs` and returns from the current function if `rhs` returns an `Exception`
