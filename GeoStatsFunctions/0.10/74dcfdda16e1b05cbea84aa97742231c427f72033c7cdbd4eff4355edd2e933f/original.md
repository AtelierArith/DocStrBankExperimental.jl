```
GaussianTransiogram(; range, proportions)
```

A Gaussian transiogram with `range` in length units, and categorical `proportions`.

```
GaussianTransiogram(; ranges, rotation, proportions)
```

Alternatively, use multiple `ranges` and `rotation` matrix to construct an anisotropic model.

```
GaussianTransiogram(ball; proportions)
```

Alternatively, use a custom metric `ball`.
