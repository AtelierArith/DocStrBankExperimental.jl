```
@addpkg name::Symbol uuid::String
```

Register the package identified by `name` with UUID `uuid`. This package may now be used with `@import $name`.

All @addpkg statements should lie within a module's `__init__` function.

# Example

```
@addpkg CSV "336ed68f-0bac-5ca0-87d4-7b16caf5d00b"
```
