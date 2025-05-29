```
similarterm(t, f, args, symtype; metadata=nothing)
```

Create a term that is similar in type to `t`. Extending this function allows packages using their own expression types with SymbolicUtils to define how new terms should be created. Note that `similarterm` may return an object that has a different type than `t`, because `f` also influences the result.

## Arguments

  * `t` the reference term to use to create similar terms
  * `f` is the operation of the term
  * `args` is the arguments
  * The `symtype` of the resulting term. Best effort will be made to set the symtype of the resulting similar term to this type.
