```
@genexport(type [, importconstruct_arg])
```

Generates the import/export functions for the given type (necessary for `AbstractParticle`s`and`AbstractParams`).

The second, optional argument is for the convenience of not having to call `@importconstruct` separately in case it is needed (see [@importconstruct](@ref) for details):

```julia
@genexport MyType kw=false
```

is equivalent to:

```julia
@importconstruct MyType kw=false
@genexport MyType
```

For more information on the export system, consult the InPartS manual.
