```
update!(model, q = nothing, b = nothing)
```

Updates the model data for `b` or `q`. This can be done without refactoring the KKT matrix. The vectors will be appropriatly scaled.
