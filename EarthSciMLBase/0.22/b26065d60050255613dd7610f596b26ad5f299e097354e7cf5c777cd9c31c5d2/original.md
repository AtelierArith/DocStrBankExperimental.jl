```julia
operator_compose(a, b)
operator_compose(a, b, translate)

```

Compose to systems of equations together by adding the right-hand side terms together of equations that have matching left-hand sides. The left hand sides of two equations will be considered matching if:

1. They are both time derivatives of the same variable.
2. The first one is a time derivative of a variable and the second one is the variable itself.
3. There is an entry in the optional `translate` dictionary that maps the dependent variable in the first system to the dependent variable in the second system, e.g. `Dict(sys1.sys.x => sys2.sys.y)`.
4. There is an entry in the optional `translate` dictionary that maps the dependent variable in the first system to the dependent variable in the second system, with a conversion factor, e.g. `Dict(sys1.sys.x => sys2.sys.y => 6)`.
