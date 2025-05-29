```
Model(f, args::NamedTuple[, defaults::NamedTuple = ()])
```

Create a model with evaluation function `f` and missing arguments deduced from `args`.

Default arguments `defaults` are used internally when constructing instances of the same model with different arguments.
