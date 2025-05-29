```
@contextvar var[::T] [= default]
```

Declare a context variable named `var`.  The type constraint `::T` and the default value `= default` are optional.  If the default value is given without the type constraint `::T`, its type `T = typeof(default)` is used.

!!! warning
    Context variables defined outside a proper package does not work with `Distributed`.


# Examples

Top-level context variables needs to be declared in a package:

```julia
module MyPackage
@contextvar cvar1
@contextvar cvar2 = 1
@contextvar cvar3::Int
end
```
