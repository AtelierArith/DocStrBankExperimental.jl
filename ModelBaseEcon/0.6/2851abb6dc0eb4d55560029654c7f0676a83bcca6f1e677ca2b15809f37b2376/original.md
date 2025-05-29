```
selective_linearize!(model)
```

Instruct the model instance to use selective linearization. Only equations annotated with `@lin` in the model definition will be linearized about the current steady state solution while the rest of the eq
