```
flatten(::A{A})::A = flatmap(identity, a)
```

`flatten` gets rid of one level of nesting. Has a default fallback to use `flatmap`.
