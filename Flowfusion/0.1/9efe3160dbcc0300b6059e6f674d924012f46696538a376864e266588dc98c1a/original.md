```
dense(X::DiscreteState; T = Float32)
```

Converts `X` to an appropriate dense representation. If `X` is a `DiscreteState`, then `X` is converted to a `CategoricalLikelihood` with default eltype Float32. If `X` is a "onehot" CategoricalLikelihood then `X` is converted to a fully dense one.
