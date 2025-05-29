```
domainspace(op::Operator)
```

Return the domain space of `op`.  That is, `op*f` will first convert `f` to a `Fun` in the space `domainspace(op)` before applying the operator.
