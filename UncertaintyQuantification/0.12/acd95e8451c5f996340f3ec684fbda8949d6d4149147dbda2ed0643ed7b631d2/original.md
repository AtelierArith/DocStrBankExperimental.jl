```
Model(f::Function, name::Symbol)
```

The function `f` must accept a `DataFrame` and return the result of the model for each row in the `DataFrame` as a vector. The `name` is used to add the output to the `DataFrame`.
