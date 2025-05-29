```
debang(f!::Function, ex=nothing)
```

Convert a mutating function into non-mutating form.

`f!` must be a two-argument mutating function, which writes the result into its first argument. The result of `debang` is then `f`, a single-argument non-mutating function that allocates and returns the result. Schematically, `f!(out, x)` becomes `f(x)`.

When the type, size and shape of `out` is the same as those of `x`, it is enough to supply just `f!`. When `f` is called, output will be allocated as `similar(x)`.

When the type, size and/or shape of `out` are different from those of `x`, then an example instance of the correct type with the correct size and shape for the output must be supplied, as debang's `ex` argument. When `f` is called, output will be allocated as `similar(ex)`. The `ex` instance will be automatically kept alive by the lexical closure of `f`.

# Note

While the type of `out` is known at compile time, the size and shape are typically runtime properties, not encoded into the type. For example, arrays have the number of dimensions as part of the type, but the length of each dimension is only defined at run time, when an instance is created. This is why the `ex` argument is needed.

# Etymology

By convention, mutating functions are marked with an exclamation mark, a.k.a. bang. This function takes away the bang.
