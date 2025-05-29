```
entry()
entry(state)
```

When used in a finite-state machine, this operator returns true at the first tick when the state is active, and false otherwise.

When used to query the entry of the enclosing state, the method without arguments is used, when used to query the entry of another state, the state is passed as an argument.

This can be used to perform a unique action when entering a state.
