```
@obsex([name =] expression)
```

Define observable expressions, which are simple combinations of knonw states/parameters/observables. `@obsex(...)` returns an `ObservableExpression` which can be used as an symbolic index. This is mainly intended for quick plotting or export of common "derived" variables, such as the argument of a 2-component complex state. For example:

```
sol(t; idxs=@obsex(arg = atan(VIndex(1,:u_i), VIndex(1,:u_r))]
sol(t; idxs=@obsex(δrel = VIndex(1,:δ) - VIndex(2,:δ)))
```
