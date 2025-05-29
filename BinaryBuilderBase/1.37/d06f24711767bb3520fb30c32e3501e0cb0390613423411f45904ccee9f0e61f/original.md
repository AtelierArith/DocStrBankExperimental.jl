An `ExecutableProduct` is a [`Product`](@ref) that represents an executable file.

On all platforms, an ExecutableProduct checks for existence of the file.  On non-Windows platforms, it will check for the executable bit being set.  On Windows platforms, it will check that the file ends with ".exe", (adding it on automatically, if it is not already present).

---

```
ExecutableProduct(binname, varname::Symbol, dir_path="bin")
```

Declares an `ExecutableProduct` that points to an executable located within the prefix.  `binname` specifies the basename of the executable, `varname` is the name of the variable in the JLL package that can be used to call into the library.  By default, the library is searched in the `bindir`, but you can specify a different directory within the prefix with the `dir_path` argument.
