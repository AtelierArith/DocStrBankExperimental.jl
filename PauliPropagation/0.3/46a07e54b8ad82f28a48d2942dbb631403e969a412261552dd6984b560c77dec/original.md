```
wrapcoefficients(psum::PauliSum, PathPropertiesType<:PathProperties)
```

Wrap the coefficients of a `PauliSum` into a custom `PathProperties` type. For anything that is not natively supported by the library, you can subtype `PathProperties`. A one-argument constructor of the custom `PathProperties` type from a coefficient must be defined.
