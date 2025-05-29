```
has_symbolic_var(eqs, var)
```

Return `true` if symbolic variable `var` exists in the equation(s) `eq`, `false` otherwise. This works for either `@parameters` or `@variables`. If `var` is a `Symbol` isntead of a `Num`, all variables are converted to their names and equality is checked on the basis of the name only.

```
has_symbolic_var(model, var)
```

When given a MTK model (such as `ODESystem`) search in *all* the equations of the system, including observed variables.
