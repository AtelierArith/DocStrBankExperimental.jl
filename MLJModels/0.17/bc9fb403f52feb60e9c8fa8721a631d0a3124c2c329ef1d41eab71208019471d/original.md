```
models(; wrappers=false)
```

List all models in the MLJ registry. Here and below *model* means the registry metadata entry for a genuine model type (a proxy for types whose defining code may not be loaded). To include wrappers and other composite models, such as `TunedModel` and `Stack`, specify `wrappers=true`.

```
models(filters...; wrappers=false)
```

List all models `m` for which `filter(m)` is true, for each `filter` in `filters`.

```
models(matching(X, y); wrappers=false)
```

List all supervised models compatible with training data `X`, `y`.

```
models(matching(X); wrappers=false)
```

List all unsupervised models compatible with training data `X`.

### Example

If

```
task(model) = model.is_supervised && model.is_probabilistic
```

then `models(task)` lists all supervised models making probabilistic predictions.

See also: [`localmodels`](@ref).
