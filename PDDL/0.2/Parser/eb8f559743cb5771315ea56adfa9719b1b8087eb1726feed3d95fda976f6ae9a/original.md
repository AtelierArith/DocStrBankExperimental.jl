```
pddl"..."
```

Parse string `"..."` to PDDL construct.

When parsing PDDL formulae, the variable `x` can be interpolated into the string using the syntax `$x`. For example, `pddl"(on $x $y)"` will parse to `Compound(:on, Term[x, y])` if `x` and `y` are [`Term`](@ref)s.

Julia expressions can be interpolated by surrounding the expression with curly braces, i.e. `${...}`.
