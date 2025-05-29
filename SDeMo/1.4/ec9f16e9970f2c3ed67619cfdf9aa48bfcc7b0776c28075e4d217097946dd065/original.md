```
WhiteningTransform
```

The whitening transformation is a linear transformation of the input variables, after which the new variables have unit variance and no correlation. The input is transformed into white noise.

Because this transform will usually keep the first variable "as is", and then apply increasingly important perturbations on the subsequent variables, it is sensitive to the order in which variables are presented, and is less useful when applying tools for interpretation.

This is an alias for `MultivariateTransform{Whitening}`.
