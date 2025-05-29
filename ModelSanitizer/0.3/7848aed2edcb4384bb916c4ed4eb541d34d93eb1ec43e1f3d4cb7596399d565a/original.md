````
Sanitize a model.

If your model is stored in `m` and your data are stored in `x1`,
`x2`, `x3`, etc. then you can sanitize your model with:
```julia
sanitize!(Model(M), Data(x1), Data(x2), Data(x3), ...)
```
````
