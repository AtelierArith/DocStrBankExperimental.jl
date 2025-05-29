```
WrongManifoldException{InputManifold, DesiredManifold, Algorithm} <: Exception
```

This error is thrown when an `Algorithm` is called with a manifold that it was not designed for.

It's mainly thrown when constructing `SingleManifoldAlgorithm` types.
