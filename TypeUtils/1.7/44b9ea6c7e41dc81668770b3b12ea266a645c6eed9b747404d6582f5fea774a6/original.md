```
TypeUtils.Unsupported(T::DataType...)
```

yields an union of types `T...` and of type `Unsupported`. Such an union can be used to mark unsupported argument type(s) and yet define a method applicable with that type(s) (presumably a method that throws an instructive error) and which can be extended later with the same signature except that with `Unsupported(T...)` replaced by `T...`. This trick avoids conflicts that prevent pre-compilation with package extensions.

For example, in the main package:

```julia
some_method(some_arg::Unsupported{SomeType}) =
    error("package `SomeOtherPackage` has not yet been loaded")
```

and in the extension (e.g. automatically loaded when using `SomeOtherPackage`):

```julia
some_method(some_arg::SomeType) = do_something_with(some_arg)
```
