```
GenerativeDerivativeMethod <: AbstractDerivativeMethod
```

An abstract type for derivative evaluation method types that will require support  generation when employed (e.g., internal node points associated with orthogonal  collocation). Such methods can be used with derivatives that depend on independent  infinite parameters, but cannot be used for ones that depend on dependent parameters.
