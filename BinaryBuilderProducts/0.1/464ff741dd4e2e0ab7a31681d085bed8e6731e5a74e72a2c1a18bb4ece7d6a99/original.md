```
LibraryProduct(paths::Vector{String}, varname::Symbol;
               deps=LibraryProduct[],
               dlopen_flags=Symbol[])
```

Declares a `LibraryProduct` that points to a library located within the prefix. `paths` contain valid paths for this library, `varname` is the name of the variable in the JLL package that can be used to call into the library.  The flags to pass to `dlopen` can be specified as a vector of `Symbols` with the `dlopen_flags` keyword argument.

Each element of `path` takes the form `[dirname/]basename[.versioned-ext]` where `dirname` and `versioned-ext` are optional and can be omitted. Accordingly, the following three paths will all find the same library:

  * `lib/libnettle.so.6`
  * `lib/libnettle`
  * `libnettle.so.6`
  * `libnettle`

On non-Windows targets, omitting `dirname` will automatically prepend `lib`, while on Windows targets `bin` will be prepended.  Omitting the versioned extension will allow any version of the library to be used (usually not a problem as there's typically only one version of a library at a time).
