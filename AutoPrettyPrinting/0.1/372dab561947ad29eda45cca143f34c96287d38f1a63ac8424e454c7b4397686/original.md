```
PPrintContext(io::IO, [mime::MIME])
```

Create a `PPrintContext` that wraps a given stream. 

Subsequent calls to `Base.show(context::PPrintContext, ::MIME, x)` will use the pretty printing machinery provided in this package to render `x`. This type is useful primarily when `x` has a `custom_tile` method defined (or provided by this package), but the primary `Base.show` methods are defined outside of this package and should not be overridden. 

Additionally, if a `mime::MIME` type is provided, subsequent calls to `Base.show(context::PPrintContext, x)` will dispatch using the provided `mime` instance. 
