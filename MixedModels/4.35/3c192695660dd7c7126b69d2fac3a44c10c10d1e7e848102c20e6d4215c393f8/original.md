```
leverage(::LinearMixedModel)
```

Return the diagonal of the hat matrix of the model.

For a linear model, the sum of the leverage values is the degrees of freedom for the model in the sense that this sum is the dimension of the span of columns of the model matrix.  With a bit of hand waving a similar argument could be made for linear mixed-effects models. The hat matrix is of the form $[ZΛ X][L L']⁻¹[ZΛ X]'$.
