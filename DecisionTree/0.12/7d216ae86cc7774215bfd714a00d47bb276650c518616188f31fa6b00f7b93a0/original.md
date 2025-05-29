```
build_forest(model, labels, features, options...; keyword_options...)
```

Return an updated version of `model` with additional `n_trees=options[2]` added to the forest. Here `options` and `keyword_options` are as for the regular `build_forest` method, which excludes the `model` argument.

Even if training data is the same in all `build_forest` calls, it is not practically possible to guarantee adding trees in steps is identical to adding them all at once, because of the way random number generators are generated and used. But in all other respects these approaches are equivalent.

# Example

```
features, labels = load_data("iris")
features = float.(features)
labels = string.(labels)
```

The call

```
model = build_forest(labels, features, 2, 200) # n_trees = 200
```

is approximately equivalent to

```
model1 = build_forest(labels, features, 2, 150) # n_trees = 150
model = build_forest(model1, labels, features, 2, 50) # n_trees = 50
```
