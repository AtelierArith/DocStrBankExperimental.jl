```
ShowParams
```

An `AbstractShow` wrapper for showing the type parameters of the type of the wrapped object.

The underlying type is determined recursively, so if an `AbstractShow` object is wrapped, the type of the (deepest) wrapped object will be shown.

## Constructors

  * `ShowParams(o; show_module=:context, kw...)`

## Arguments

  * `o`: the object to be wrapped.
  * `show_module::Symbol`: whether to show the modules of the type parameters, see [`ShowType`](@ref) for available options.
  * `kw`: Any other keyword arguments accepted by [`ShowList`](@ref)
