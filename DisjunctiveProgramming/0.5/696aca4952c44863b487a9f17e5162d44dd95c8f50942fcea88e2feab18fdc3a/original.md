```
@disjunctions(model, args...)
```

Adds groups of disjunctions at once, in the same fashion as the `@disjunction` macro.

The model must be the first argument, and multiple disjunctions can be added on multiple  lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the disjunctions that were defined.

## Example

`julia model = GDPModel(); @variable(model, w); @variable(model, x); @variable(model, Y[1:4], LogicalVariable); @constraint(model, [i=1:2], w == i, Disjunct(Y[i])); @constraint(model, [i=3:4], x == i, Disjunct(Y[i])); @disjunctions(model, begin     [Y[1], Y[2]]     [Y[3], Y[4]] end);``
