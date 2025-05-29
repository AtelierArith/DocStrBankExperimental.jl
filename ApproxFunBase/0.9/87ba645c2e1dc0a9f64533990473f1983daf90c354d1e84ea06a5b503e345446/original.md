```
rangespace(op::Operator)
```

Return the range space of `op`.  That is, `op*f` will return a `Fun` in the space `rangespace(op)`, provided `f` can be converted to a `Fun` in `domainspace(op)`.
