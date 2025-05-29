```
wrapcoefficients(pstr::PauliString, PathPropertiesType<:PathProperties)
```

Wrap the coefficient of a `PauliString` into a custom `PathProperties` type. For anything that is not natively supported by the library, you can subtype `PathProperties`. A one-argument constructor of the custom `PathProperties` type from a coefficient must be defined.
