```
expression_new(expression_type::Type, operation, children, metadata)
```

Returns an expression whose type is based on `expression_type`, but with `children` as its immediate children and with `operation` as its top-level operation.

The `metadata` argument may carry additional necessary data. Use `nothing` as the default.
