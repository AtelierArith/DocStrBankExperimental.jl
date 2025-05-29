```
@import pkg1, pkg2...
@import pkg1 as name1, pkg2 as name2...
@import pkg: foo, bar...
@import pkg: foo as bar, bar as baz...
```

Fetch modules previously registered with `@addpkg`, and import them into the current namespace. This macro tries to largely mirror the syntax of `using`.

For the sake of type inference, it is assumed that all bindings that start with a lower case letter are functions, and bindings that start with an upper case letter are types. Exceptions must be manually annotated with type assertions.

If a required package had to be loaded for the `@import` statement, a `PkgRequiredRerunNeeded` singleton will be returned.

# Example

```julia
@import pkg
pkg.dothing(...)
# Alternative form
@import pkg: dothing
dothing(...)
```
