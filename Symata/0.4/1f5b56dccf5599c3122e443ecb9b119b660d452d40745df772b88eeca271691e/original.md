```
symatamath()
```

defines Base methods for arithmetic operators `*`, `+`, `-`, `^` between `Symbols` and between `Symbols` and `Numbers`. `symatamath()` is *not* necessary when running Symata and using J(expr) to evaluate Julia code.  `J()` evaluates in the Symata module where these methods are already defined.  `symatamath()` is useful in Julia mode where expressions are evaluated in  `Main`.

These methods are not defined in `Main` by default because defining `Base` methods between core Julia objects could conflict with future versions of Julia.
