```
Style
```

A struct containing metadata for specifying the "style" (i.e. color and other attributes used when printing to some displays) of an object to be shown.

Styles can be used in `show` or `print` with `show(io, 𝔰, x)` or `print(io, 𝔰, x)` where `𝔰` is a `Style` and `x` is any other object.

## Constructors

  * `Style(color, bold)`
  * `Style(;color=:normal, bold=false)`

## Arguments

  * `color`: The color to print or show with as it would be provided to `printstyled`.  See `printstyled`   documentation for allowed color specifiers (these are either `Symbol` e.g. `:red` or integers).
  * `bold`: A boolean specifying whether the object should be shown with bold text.
