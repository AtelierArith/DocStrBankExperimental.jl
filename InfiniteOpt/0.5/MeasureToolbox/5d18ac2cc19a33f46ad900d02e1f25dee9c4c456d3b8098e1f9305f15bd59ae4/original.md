```
Quadrature <: AbstractUnivariateMethod
```

A general integral evaluation method that will automatically select the appropriate quadrature method to approximate the integral. Please note that this will generate a unique set of parameter supports and will ignore existing supports when the integral is evaluated and thus should be used with caution. However, this method is able to handle infinite and semi-infinite integral domains. This is not compatible with individual dependent parameters. Contains no fields.
