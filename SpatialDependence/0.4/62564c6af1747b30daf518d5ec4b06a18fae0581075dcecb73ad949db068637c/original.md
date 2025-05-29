```
wtransform!(W::SpatialWeights, style::Symbol)
```

In-place transformation of the weights using the specified $style$.

# Weights transformation

`style` can be one of the following:

  * `:binary`: 1 if neighbor, 0 if not.
  * `:row`: row-standardized. Each row sum equals one.
