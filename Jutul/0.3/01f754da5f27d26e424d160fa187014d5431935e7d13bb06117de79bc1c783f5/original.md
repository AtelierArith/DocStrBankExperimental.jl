```
update_state_dependents!(storage, model, dt, forces; time = NaN, update_secondary = true)
```

Perform updates of everything that depends on the state: A full linearization for the current primary variables.

This includes properties, governing equations and the linearized system itself.
