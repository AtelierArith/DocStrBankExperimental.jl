```
apply(op, ::State; limits::Limits)
apply(mps, ::State; limits::Limits)
apply(op, ::Simulation; limits::Limits)
```

Apply the given gates to the state and truncate the result according to limits. It is much more efficient to apply all the gates in a single call to apply.

# Examples

```
apply(CZ(1,3)*H(2)*CNOT(3,4), state)
```
