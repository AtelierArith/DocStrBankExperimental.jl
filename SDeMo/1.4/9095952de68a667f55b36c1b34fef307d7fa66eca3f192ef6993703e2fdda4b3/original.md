```
holdout(y, X; proportion = 0.2, permute = true)
```

Sets aside a proportion (given by the `proportion` keyword, defaults to `0.2`) of observations to use for validation, and the rest for training. An additional argument `permute` (defaults to `true`) can be used to shuffle the order of observations before they are split.

This method returns a single tuple with the training data first and the validation data second. To use this with `crossvalidate`, it must be put in `[]`.
