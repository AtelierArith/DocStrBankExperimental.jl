```
RandomVariable{T}
```

A RandomVariable can be "assigned" to different model parameters. Its value can be used directly or applied by adding to, or multiplying by,  reference values for the indicated parameter. Note that the distribution must be instantiated, e.g., call as RandomVariable(:foo, Normal()), not RandomVariable(:foo, Normal).
