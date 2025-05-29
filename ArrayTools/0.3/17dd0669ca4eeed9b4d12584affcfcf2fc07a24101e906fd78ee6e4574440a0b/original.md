```
noneof(f, args...) -> bool
```

checks whether predicate `f` returns `false` for all argument `args...`, while

```
noneof(args...) -> bool
```

checks whether all argument `args...` are false.

See also `any`, [`allof`](@ref), [`noneof`](@ref).
