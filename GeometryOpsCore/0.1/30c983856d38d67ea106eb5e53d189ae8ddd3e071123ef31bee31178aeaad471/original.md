```
AutoManifold()
```

The `AutoManifold` is a special manifold that automatically selects the best manifold for the operation. It does not carry any parameters, nor does it indicate anything about the nature of the space.

This gets resolved to a specific manifold when an operation is applied, using the `format` method.  
