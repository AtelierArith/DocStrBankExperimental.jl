```
Print
```

An `AbstractShow` wrapper that forces the underlying object to be shown using the `print` method.  That is, calling `show(io, Print(x))` is equivalent to `print(io, x)`. This is particularly useful for passing arbitrary strings to functions in the `ShowCases` module.

## Constructors

  * `Print(x)`; where `x` is the object to be wrapped.

## Examples

```
julia> Print("spock")
spock

```

Note the lack of printed `"` characters.
