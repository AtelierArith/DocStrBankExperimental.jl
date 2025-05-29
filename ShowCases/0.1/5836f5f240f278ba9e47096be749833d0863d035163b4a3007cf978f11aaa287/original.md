```
ShowType
```

An `AbstractShow` wrapper for showing a type with some relevant options, such as whether the module should be shown.

Note that it is expected that `ShowType` is only used to show `Type` objects, though for generality it does not forbid the printing of other objects.

See `ShowTypeOf` for showing the type *of* the wrapped object.

## Constructors

  * `ShowType(o; show_module=:context)`

## Arguments

  * `o`: the object to be wrapped.
  * `show_module::Symbol`: (*valid options:* `:always`, `:never`, `:context`) specifies whether the module name should be shown.   If `:context`, the default behavior from `Base` will be used in which the printing of the module is contextual.   If `:never`, the module will never be shown.  If `:always`, it will always be shown.
