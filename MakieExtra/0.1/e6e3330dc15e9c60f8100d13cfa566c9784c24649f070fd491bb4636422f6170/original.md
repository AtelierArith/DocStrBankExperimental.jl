```
@lift expr
@lift expr::T
```

Similar to `Makie.@lift`, but:

  * supports specifying the target observable type `T`;
  * works without any observables at all, resulting in a no-op.
