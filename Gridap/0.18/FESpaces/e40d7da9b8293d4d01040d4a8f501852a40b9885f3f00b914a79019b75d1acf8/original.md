```
uh, cache = solve!(uh,solver,op)
```

This function changes the state of the input and can render it in a corrupted state. It is recommended to rewrite the input `uh` with the output as illustrated to prevent any issue.
