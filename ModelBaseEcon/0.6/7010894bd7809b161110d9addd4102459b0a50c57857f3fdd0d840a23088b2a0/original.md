```
assign_sstate!(model, collection)
assign_sstate!(model; var = value, ...)
```

Assign a steady state solution from the given collection of name=>value pairs into the given model. 

In each pair, the value can be a number in which case it is assigned as the level and the slope is set to 0. The value can also be a `Tuple` or a `Vector` in which case the first two elements are assigned as the level and the slope. Finally, the value can itself be a name-value collection (like a named tuple or a dictionary) with fields `:level` and `:slope`. Variables whose steady states are found in the collection are assigned and also marked as solved.
