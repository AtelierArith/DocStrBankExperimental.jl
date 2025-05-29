```
@collapse y1 = expr1 y2 = expr2 ... [@if condition], [by(group1, group2, ...)]
```

Collapse `df` by evaluating expressions `expr1`, `expr2`, etc. If `condition` is provided, the operation is executed only on rows for which the condition is true. If `by` is provided, the operation is executed by group.
