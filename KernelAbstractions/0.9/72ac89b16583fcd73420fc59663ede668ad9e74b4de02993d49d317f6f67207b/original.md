```
@uniform expr
```

`expr` is evaluated outside the workitem scope. This is useful for variable declarations that span workitems, or are reused across `@synchronize` statements.
